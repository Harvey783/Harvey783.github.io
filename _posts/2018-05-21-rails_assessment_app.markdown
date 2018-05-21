---
layout: post
title:      "Rails Assessment App"
date:       2018-05-21 21:49:20 +0000
permalink:  rails_assessment_app
---


I really didn't have to much difficulty with the Rails Assessment project. I think this was largely due to my ability to build upon what I did for my Sinatra Assessment App. That being said one area that did prove difficult was getting the Facebook login to work. Facebook recently started to enforce the use of HTTPs, even in development, so I needed to add that funtionality to my Rails App by creating a SSL via `openssl req -x509 -sha256 -nodes -newkey rsa:2048 -days 365 -keyout localhost.key -out localhost.crt`. Once the SSL is created you bind it to the rails server like through `rails s -b 'ssl://localhost:3000?key=path/to/file/localhost.key&cert=path/to/file/localhost.crt'`. Doing this enabled my Facebook login to finally work. Hopefully this helps someone in the future.
