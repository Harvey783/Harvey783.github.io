---
layout: post
title:      "Reversing Integers"
date:       2019-08-25 00:00:53 +0000
permalink:  reversing_integers
---

A common question asked in technical interviews involves reversing integers. Two straightforward solutions for this are the following:

###### Solution #1

```
 function reverseInt(n) {
   const reversed = n
     .toString()
     .split('')
     .reverse()
     .join('');
   if (n < 0) {
     return parseInt(reversed) * -1;
   }
   return parseInt(reversed);
 }
```

###### Solution #2

```
function reverseInt(n) {
  const reversed = n
    .toString()
    .split('')
    .reverse()
    .join('');
  return parseInt(reversed) * Math.sign(n);
}
```
