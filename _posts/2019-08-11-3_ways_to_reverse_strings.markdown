---
layout: post
title:      "3 Ways to Reverse Strings"
date:       2019-08-11 20:38:31 +0000
permalink:  3_ways_to_reverse_strings
---


You never know when you'll need it but when you do, here's thee ways to do it.

--- Splt, Reverse, Join ---

Split the string into an array of substrings, call reverse on the newly created array, and then join the array back into a string.

```
reverse = string => {
  return string
    .split('')
    .reverse()
    .join('');
};
```


--- For Of ---

Create an empty string, iterate through it, and and for each character in the string add it to the start of the empty string.

```
reverse = string => {
  let reversed = '';
  for (let character of string) {
    reversed = character + reversed;
  }
  return reversed;
};
```


--- Reduce ---

Turn a string into an array with the split function, and then use the reduce method, which takes all the values of an array and condenses them into a single value. When reduce first runs it takes the empty string starting argument and passes into the arrow function as the first argument. Whatever gets returned from that inner arrow function then gets used as the starting argument for every successive run of the function. The function runs one time for every element or character and adds it to the string.

```
function reverse(string) {
  string.split('').reduce((reversed, character) => 
  character + reversed, '');
}
```


