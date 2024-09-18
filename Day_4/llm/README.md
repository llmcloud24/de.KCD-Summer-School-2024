## Day 4: Web App Example: OAuth + Open WebUI + Ollama

We have an example set up that you can visit here: https://foooauth.llmcloud24.bihealth.org/

### What is happening here?

### How do we deploy them?

#### Pre-requisites:

If you intend to do this yourself, you will need the following things:
 - Request a subdomain for your VM from one of the BIH people
 - Create a New GitHub OAuth App here: https://github.com/settings/developers with the following settings:
   - Application Name: can be anything you want
   - Homepage URL: `https://SOMETHING.llmcloud24.bihealth.org/`
   - Authorization callback URL: `https://SOMETHING.llmcloud24.bihealth.org/oauth2/callback`
   - You can leave the **Enable Device Flow** unchecked
 - After this, you will get a **Client secrets**, make sure you note this down somewhere, or it will disappear!
 - You can also find your **Client ID** on the same page, you need both of these.
 - In addition, generate a **cookie secret** that we will use later, so note it down somewhere: `openssl rand -hex 16`
