---
layout: post
title:      "Modular Pattern Fight Sim"
date:       2019-06-07 20:52:07 +0000
permalink:  modular_pattern_fight_sim
---


I was playing around with Module Patterns earlier today and somehow ended up with this super, scientific fight simulator. Figured I'd share for levity's sake.  The basic approach is to use an immediately invoked function expression (IIFE) that returns an object. An IIFE is a function expression that is defined and then called immediately to produce a result. You  accomplish this by creating closure functions as object methods. Closures are simply functions that access data outside their own scope. 

```
const fightSim = (function() {
  function fight(contestantOne, contestantTwo) {
    const attackOne = (Math.random() * contestantOne.length).toFixed(2);
    const attackTwo = (Math.random() * contestantTwo.length).toFixed(2);
    return attackOne > attackTwo
      ? `${contestantOne} Beats ${contestantTwo}. All Hail ${contestantOne}!!!`
      : `${contestantTwo} Beats ${contestantOne}. All Hail ${contestantTwo}!!!`;
  }
  return {
    fight
  };
})();
console.log(fightSim.fight('Bear', 'Shark'));
// Bear Beats Shark. All Hail Bear!!!
```
