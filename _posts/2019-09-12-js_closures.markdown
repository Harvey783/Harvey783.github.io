---
layout: post
title:      "JS Closures"
date:       2019-09-12 22:02:03 -0400
permalink:  js_closures
---


A closure in JavaScript is simply when you nest one function inside another function, and then either return or assign it. Take the example below. The closure gets returned when publicFunction() is returned.

```
*const publicFunction = () => {
  let private = "I'm hidden ";
  
  const privateFunction = () => {
    return private += " but now can be accessed and modified through closures.";
  }
  return privateFunction();
}

console.log(private)    //  Undefined because private was defined locally within publicFunction() 
outerFunction()  // I'm hidden but now can be accessed and modified through closures.
```

