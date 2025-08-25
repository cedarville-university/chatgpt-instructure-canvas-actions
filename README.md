# ChatGPT Custom GPT Oauth Authentication Setup Instructions

## Create a new GPT Action
Set up a new GPT in ChatGPT by going to **My GPTs** and clicking **Create a New GPT** 

Set up a new action in your GPT by going to the **Configure** Tab and choosing **Create a new action**

Click the **⛭** icon next to the Authentication field, and choose OAuth. 

## Create a Canvas Developer Key

As a Instructure Canvas Admin, use [these instructions to create a Developer Key](https://community.canvaslms.com/t5/Admin-Guide/How-do-I-add-a-developer-API-key-for-an-account/ta-p/259). Set the **Key Name** and **Owner Email** fields, and leve the rest blank/default for now 

## Set up OAuth Authentication to Canvas
Back in your new custom GPT's actions Authentication page:
* Copy the Key ID froj the Details column (long number like 136680000000000591) into the **Client ID** field in your GPT action's Authentication window
* Copy the Secret Key (long string of letters) into the **Client Secret** field in your GPT action's Authentication window
* Set the Authorization URL: `https://yourdomain.instructure.com/login/oauth2/auth`
* Set the Token URL: `https://yourdomain.instructure.com/login/oauth2/token` 
  _(substitue your Canvas tenant's FQDN in place of **yourdomain.instructure.com**)_
* Leave **Scope blank**, unless you are enforcing Scopes in your Canvas Developer Key (see [Scopes](#scopes))
* Set **Token Exchange Method** to **Default (POST Request)**
* Save the authentication parameters\

## Import YAML and Instructions

Still in the Actions page of your custom GPT, copy the raw YAML from [instructure-actions.yml](./instructure-actions.yml) into the Schema field. 

Edit the following object in the YAML: 

```yaml
servers:
  - url: https://yourdomain.instructure.com
```
Change the URL to the correct URL for your Canvas tenant. 

Ensure that each of the **path** objects shows up on their own line below the Schema field. 

Click the back button to get out of the **Edit Actions** pane (back to the **Configure** tab of your custom GPT and copy the raw Markdown text from [instructions.md](./instructions.md) into the GPT's instructions field. 

## Set up Callback URLs & Enable in Canvas

Copy the Callback URL from the box below the actions area on **Configure** tab of your custom GPT. 

Back in the Canvas Developer Keys page, edit your Developer Key, and add the Callback URL as a Redirect URL. It will look something like this: 
`https://chat.openai.com/aip/g-b6c923exxxxxxxxxxxxxxxxxxxxxxxx/oauth/callback`

For some backwards compatibility with other OpenAI domains, add some whitespace after the first URL, and add a version with the domain chatgpt.com:
`https://chatgpt.com/aip/g-b6c923exxxxxxxxxxxxxxxxxxxxxxxx/oauth/callback`
(note: this callback URL is specific to each custom GPT you create, but you can add as many callback URLs as you want, separated by whitespace characters.)

Save the Developer Key, and use the switch on the main Developer Keys page to enable it.

## Try your first Chat

A good starting place to test the functionality of this GPT action is the following chat: 
`what courses am I in?`

ChatGPT should display a **login with yourdomain.instructure.com** button that will start the OAuth flow. 

Once your OAuth flow is complete, the GPT should interact with your Canvas tenant's apis to display a list of courses. 

If you go to the Actions pane in your custom GPT, there's also a **Test** button next to each endpoint that will give you a debug output of how ChatGPT used the action, and what it returned. 

## Potential Problems

1. Having mistakes in your YAML may cause authentication to break in odd and unpredictable ways. Having query parameters hard-coded in your API paths is a good example. It's not caught by the YAML linter built into the actions page, but it absolutely breaks authentication.
1. If you don't enable the Developer key (or don't add the redirect URL, you'll get a message like "
## Scopes

No Information here about enabling scopes yet. If you know how scopes work in Canavs, please send us a PR. 
