---
layout: post
title:      "Common JS Capitalization Question"
date:       2019-09-29 12:25:34 -0400
permalink:  common_js_capitalization_question
---


A common question asked in technical interviews involves capitalization. It basically requires creating a function that capitalizes the first letter of each word in a string before returning the capitalized string. So the string "capitalize me please" would return to "Capitalize Me Please". What would a function like this look like?

```
function capitalize(str) {
  const words = [];
	
  for (let word of str.split(' ')) {
    words.push(word[0].toUpperCase() + word.slice(1));
  }
	
  return words.join(' ');
}
```

So first you create an empty array. Then Split the input string by spaces to get an array. Next Uppercase the first letter of the word and Join the first letter with the rest of the string. Then Push result into the array before you Join 'words' into a string and return it.
