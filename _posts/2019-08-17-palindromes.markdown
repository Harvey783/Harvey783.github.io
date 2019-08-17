---
layout: post
title:      "Palindromes"
date:       2019-08-17 05:18:10 +0000
permalink:  palindromes
---


A common question asked in technical interviews involves palindromes. A palindrome is simply a word that when reversed remains the same. So, an interviewer might ask, "Write a function that when given a string returns 'true' if it’s a palindrome." Two straightforward solutions for this are the following:

*Solution #1*

```
palindrome = string => {
  // Create a variable called 'reverseString' and set it equal to the string argument
  const reversedString = string
	// Split the string into an array of substrings
    .split('')
    // Reverse the array
    .reverse()
	// Join the reversed substrings together
    .join('');
  // Return true if the string argument equals reversedString
  return string === reversedString;
};
```

*Solution #2*

```
palindrome = string => {

  // Turn the string into an array and call every(). This method performs a boolean check of every item in an array.  The first argument is a callback function that will be called for every element in the array. It receives the argument 'character' which is each character from the array. The second argument taken by the callback is 'i' which is the index of the character, currently being iterated over.
	
  return string.split('').every((character, i) => {
	
	// Return a comparison of the current character to its relative at the opposite end of the array. If each character matches it returns true,
		
    return character === string[string.length - i - 1];
  });
};
```

