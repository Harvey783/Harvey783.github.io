---
layout: post
title:      "Quick LocalStorage Setup"
date:       2019-06-20 08:28:17 +0000
permalink:  quick_localstorage_setup
---


Taking advantage of and setting up JavaScript's Local Storage is pretty painless.

```
let dogs; // initialize dogs

if (localStorage.getItem('dogs') === null) {
  dogs = [];
  // If a dogs array can't be found then create one
} else {
  dogs = JSON.parse(localStorage.getItem('dogs'));
  // Otherwise parse the existing JSON string and construct the array
}

dogs.push('Ash');
dogs.push('Logan');
// Create some records and push into the array

localStorage.setItem('dogs', JSON.stringify(dogs));
// Gets the dogs array and converts it into a JSON string

console.log(dogs);
// ["Ash", "Logan"]
```
