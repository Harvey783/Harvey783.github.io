---
layout: post
title:      "Reduce's Flexibility"
date:       2019-06-16 17:34:38 +0000
permalink:  reduces_flexibility
---


The array Reduce itterator method returns a new array with values reduced to a single value. Reduce loops through an array calling a callback function. The first parameter of the callback is the total of all calculations denoted as 'acc' for accumulator. The second parameter is the current value of the array denoted as 'curr'. An initial value is also set at the end of the reduce method as well. Finally, a new array is returned that is reduced to a single value. What makes the reduce method so useful is its flebility. Take these three examples for instance.

**BASIC**
```
const numbers = [0, 1, 2, 3, 4, 5];
const total = numbers.reduce((acc, curr) => {
  acc = acc + curr;
  return acc;
}, 0);
console.log(total); 
// 15
```

**GETTING DISTINCT VALUES**
```
const colors = ['red', 'blue', 'white', 'red', 'red', 'blue'];
const distinct = colors.reduce((acc, curr) => {
  if (acc.indexOf(curr) === -1) {
    acc.push(curr);
  }
  return acc;
}, []);
console.log(distinct);
// { red, blue, white }
```

**CREATING OBJECT THAT COUNTS**
```
const colors = ['red', 'blue', 'white', 'red', 'red', 'blue'];
const types = colors.reduce((total, color) => {
  if (total[color]) {
    total[color] += 1;
  } else {
    total[color] = 1;
  }
  return total;
}, {});
console.log(types);
// { red: 3, blue: 2, white: 1 }
```

