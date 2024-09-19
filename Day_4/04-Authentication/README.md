## Day 4: Pre-Authentication Mini Hands-On

Before we proceed with the Authentication part, let's just have a mini hands-on session to set up Open WebUI, which is a web interface that can be used to chat with Ollama.

First, open the  `variables.env` in the `04-Authentication` folder. You can do so via `nano variables.env` when you're inside the folder.

The content of this file will look like this. Make sure you replace the values after the `=` sign with your own values! Make sure there are no spaces after the `=` too!
```bash
MY_ANIMAL=just_your_animal_name_for_the_domain
OLLAMA_IP=your_ollama_vm_internal_ip_10.X.X.X:PORT
OAUTH2_PROXY_CLIENT_ID=somethingsomething
OAUTH2_PROXY_CLIENT_SECRET=somethingsomething
OAUTH2_PROXY_COOKIE_SECRET=somethingsomething
```
For now let's just focus on line 2: `OLLAMA_IP=your_ollama_vm_internal_ip_10.X.X.X:PORT`. Change this to the `INTERNAL_IP:PORT` of the VM with Ollama running.

>[!TIP]
>You can use our Ollama if you don't want to use yours by changing the relevant line to `OLLAMA_IP=10.0.2.137:7869`

>[!TIP]
>If you still have your Ollama running on a VM from Day 3, you can keep using it. Find out the **internal IP** of this VM (should be something like 10.X.X.X), and if you followed the instructions from Sebastian, the port should be **11434**.
>
>Otherwise if you have lost your Ollama, you can make a new GPU VM and refer to the `04-Authentication/docker-compose-ollama.yml` file.

Save the file, and then do `source variables.env`, this will load the variables we just defined into your environment.

Then you can do `docker compose -f docker-compose-webui.yml up --build` to get your own Open WebUI service running.

To quickly check if it's running, you can do `curl localhost:8080 | grep "<title>".

If you see something like this, then it should be working:
```bash
$ curl localhost:8080 | grep "<title>"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  5971  100  5971    0     0   968k      0 --:--:-- -<title>Open WebUI</title>
    0 --:--:-- --:--:-- --:--:-- 1166k
```

Stay tuned and look into the SOCKS proxy setup session and instructions if you want to use this interface via your browser!



## Day 4: Web App Example: OAuth + Open WebUI + Ollama

We have an example set up that you can visit here: https://foooauth.llmcloud24.bihealth.org/

Pay attention to the screenshots and steps below!

![OAuth2 Proxy](../images/04-auth-1.png)
![Login using GitHub](../images/04-auth-2.png)

>[!IMPORTANT]
>Pay attention to grant access to the llmcloud24 organization before clicking the green Authorize button!
![Grant access to llmcloud24 organization and authorize your GitHub user](../images/04-auth-3.png)

### What is happening here?

When you visit the demo page, you will reach the Nginx service. This Nginx service will then forward you to the oauth2-proxy service, which presents you with the choice to access our Open WebUI web service behind the gates via GitHub login. The oauth2-proxy will let GitHub handle the user authentication process and pass on the results to our Open WebUI service.

### How do we deploy them?

#### Pre-requisites:

If you intend to do this yourself, you will need the following things:
 - Request a subdomain for your VM from one of the BIH people
 - Create a New GitHub OAuth App here: https://github.com/settings/developers with the following settings:
   - Application Name: can be anything you want
   - Homepage URL: `https://$yourAnimal.llmcloud24.bihealth.org/`
   - Authorization callback URL: `https://$yourAnimal.llmcloud24.bihealth.org/oauth2/callback`
   - You can leave the **Enable Device Flow** unchecked
 - After this, you will get a **Client secrets**, make sure you note this down somewhere, or it will disappear!
 - You can also find your **Client ID** on the same page, you need both of these.
 - In addition, generate a **cookie secret** that we will use later, so note it down somewhere: `openssl rand -hex 16`

Again, set open up the `variables.env` file to update it with the new details.

Make sure you replace the values after the `=` sign with your own values! Make sure there are no spaces after the `=` too!
```bash
MY_ANIMAL=just_your_animal_name_for_the_domain
OLLAMA_IP=your_ollama_vm_internal_ip_10.X.X.X:PORT
OAUTH2_PROXY_CLIENT_ID=somethingsomething
OAUTH2_PROXY_CLIENT_SECRET=somethingsomething
OAUTH2_PROXY_COOKIE_SECRET=somethingsomething
```

After setting the values, save the file, and run `source variables.env` again. Then, you can run `docker compose -f docker-compose-oauth.yml`.