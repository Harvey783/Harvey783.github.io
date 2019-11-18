---
layout: post
title:      "Another Common Technical Interview Question"
date:       2019-11-18 00:28:39 +0000
permalink:  another_common_technical_interview_question
---


I recently had a technical interview that asked me to solve a 'step' question. Apparentlty its pretty common. It basically asks to write a function that accepts a positive number N. The function should console log a step shape with N levels using the # character.  Make sure the step has spaces on the right hand side.

To solve this, one would do the following:

```
function steps(n) {
  // From 0 to N iterate through rows
  for (let row = 0; row < n; row++) {
    // Create an empty string 'stair'
    let stair = '';

    for (let column = 0; column < n; column++) {
      // If the current column is equal to or less than the current row
      if (column <= row) {
        stair += '#';
      } else {
        stair += ' ';
      }
    }
    console.log(stair);
  }
}
```
