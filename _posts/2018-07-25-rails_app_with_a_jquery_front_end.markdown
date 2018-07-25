---
layout: post
title:      "	Rails App with a jQuery Front End"
date:       2018-07-25 10:47:21 +0000
permalink:  rails_app_with_a_jquery_front_end
---


I found this project benefical in terms of introducing asynchronous communicat ion, and AJAX in particular. Ajax stands for Asynchronous JavaScript and XML and refers to the interaction of various technologies to retrieve and display new content without loading a new web page. 

The primary component of Ajax is the XMLHttpRequest (XHR) object. XHR allows JavaScript to send information to a web server and receive information in return, which consists roughly of five things:

1. Create an instance of the XHR Object
2. Use the XHR’s open() method to specify a method for sending the data 
     and where the data will go
3. Create a function to handle the results
4. Send request
5. Recieve response

The data the server returns is made available to the callback function to use to update the web page. Once the callback function finishes, the entire Ajax cycle is completred.
