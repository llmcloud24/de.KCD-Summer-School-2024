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

Next, make a new file called `llm.env` in the `llm` folder. You can do so via `nano llm.ev` when you're inside the `llm` folder.

The content of this file will look like this, using the 3 things that you prepared in the Pre-requisites steps. Make sure you replace the values after the `=` sign with your own values! Make sure there are no spaces after the `=` too!
```bash
MY_ANIMAL=just_your_animal_name_for_the_domain
OLLAMA_IP=your_ollama_vm_internal_ip_10.X.X.X:PORT
OAUTH2_PROXY_CLIENT_ID=somethingsomething
OAUTH2_PROXY_CLIENT_SECRET=somethingsomething
OAUTH2_PROXY_COOKIE_SECRET=somethingsomething
```
>[!TIP]
>You can use our Ollama if you don't want to use yours by changing the relevant line: `OLLAMA_IP=10.0.2.137:7869`

Then you could do `source llm.env` before running `docker compose`.
