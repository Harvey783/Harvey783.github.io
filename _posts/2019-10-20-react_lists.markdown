---
layout: post
title:      "React Lists"
date:       2019-10-20 19:28:22 +0000
permalink:  react_lists
---

Let’s say you wanted to list a series of users. To loop through them add a .map to this.state.users. Map is a higher order array method, which takes in a function. The function has a parameter that represents each user. Additionally, each user needs a unique key prop.

```
import React, { Component } from 'react';

class Users extends Component {
  state = {
    users: [
      {
        id: '1',
        login: 'Harvey783',
        avatar_url:
          'https://avatars1.githubusercontent.com/u/25391865?s=40&v=4',
        html_url: 'https://github.com/Harvey783'
      },
      {
        id: '2',
        login: 'Harvey783',
        avatar_url:
          'https://avatars1.githubusercontent.com/u/25391865?s=40&v=4',
        html_url: 'https://github.com/Harvey783'
      }
    ]
  };
  render() {
    return (
      <div>
        {this.state.users.map(user => (
          <div>key={user.id} {user.login}</div>
        ))}
      </div>
    )
  }
}

export default Users;
```
