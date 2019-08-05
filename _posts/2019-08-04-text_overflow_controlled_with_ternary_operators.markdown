---
layout: post
title:      "Text Overflow Controlled with Ternary Operators"
date:       2019-08-05 00:41:08 +0000
permalink:  text_overflow_controlled_with_ternary_operators
---


A useful trick for managing text-overflow in all those CRUD, task, blog apps is implementing a ternary operator with the JavaScript substring() method. This method pulls the characters from a string, between two specified indices, and returns the new sub string.

So lets say you wanted to limit the size of posts so a user could more easily browse through everything.An easy solution would be something like this:

`{text.length > 310 ? `${text.substring(0, 310)}...` : text}`

Here each post is limited to 310 characters. If its longer than that everything after the 310th character is cut-off and an ellipsis is added to the end. Anything under 310 characters simply renders as normal.
