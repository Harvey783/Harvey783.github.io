---
layout: post
title:      "Changing arrays to objects"
date:       2018-12-20 19:12:02 -0500
permalink:  changing_arrays_to_objecys_with_mapkeys
---

.mapKeys is a function in Lodash that takes an array and returns an object. The keys of this new object are going to be taken from each individual record inside of the array. So calling something like .mapKeys(list, "id") in the example below passes in an array and a property string of 'id' as the second arguement. This tells Lodash that whatever the value of 'id' is for any given object inside the array is now the key for that object in our new state object.

```
const list = [
  {id: 2, title: "hello"},
  {id: 5, title: "goodbye"},
  {id: 7, title: "welcome"}
]; 

_.mapKeys(list, 'id')

{
  "2":{"id":2,"title":"hello"},
  "5":{"id":5,"title":"goodbye"},
  "7":{"id":7,"title":"welcome"}
}

```

I found this extremely helpful in my postReducer when I had to return and merge my API array into a Redux state object.
```
import {FETCH_POSTS} from '../actions/types';
import _ from 'lodash';

export default (state = {}, action) => {
  switch (action.type) {
    case FETCH_POSTS:
      return { ...state, ..._.mapKeys(action.payload, 'id') };
    default:
      return state;
  }
};

```
