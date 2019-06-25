---
layout: post
title:      "OAuth 2.0 in Postman"
date:       2019-06-25 07:33:17 +0000
permalink:  oauth_2_0_in_postman
---


Postman is a great application for testing API HTTP requests and routes, and more specifically, those requiring authorization. These days, OAuth 2.0 is pretty much the industry standard in authorization protocols so its worth knowing how to properly set it up inside Postman. Luckily its a pretty straight forward process.

1. Select the Authorization tab
2. Choose OAuth 2.0 from the 'Type' menu dropdown on the left-hand side
3. Hit 'Get New Access Token' on the right

You'll then be prompted for the following information:

* **Callback URL** - In development this will be something like http://www.localhost:3001.com/auth/callback
* **Auth URL** - https://accounts.google.com/o/oauth2/auth
* **Access Token URL** - https://accounts.google.com/o/oauth2/token
* **Client ID** - The client identifier given upon app registration
* **Client Secret** - The Client Secret given upon app registration
* **Scope** - The information your requesting access to. For Google, a profile and email scope would be: https://www.googleapis.com/auth/userinfo.profile https://www.googleapis.com/auth/userinfo.email

Once all that is entered hit 'Request Token' and you're done. After that, just start up your server, login, and you're good to go.
