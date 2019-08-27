---
layout: post
title:      "Array Chunking"
date:       2019-08-27 23:09:34 +0000
permalink:  array_chunking
---


A common question asked in technical interviews involves array chunking. What is array chunking? Its dividing an array into subarrays based on a given chunk size. So if you had an array of [1,2,3,4] and a chunk size of 2 then the chunked array would be ([1,2], [3.4]). Some other exampes would be

```
chunk([1, 2, 3, 4, 5], 2) --> [[ 1, 2], [3, 4], [5]]
chunk([1, 2, 3, 4, 5], 7) --> [[ 1, 2, 3, 4, 5]]
```

So how do you go about solving a chunked array? One solution would be the following:

```
function chunk(array, size) {
  const chunked = [];
  let index = 0;

  while (index < array.length) {
    chunked.push(array.slice(index, index + size));
    index += size;
  }
  return chunked;
}
```
