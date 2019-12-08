---
layout: post
title:      "Using Environment Variables in React"
date:       2019-12-08 03:32:26 +0000
permalink:  using_environment_variables_in_react
---


Environment variables allow you to store and access sensitive information like API keys and passwords. The process is relatively straight forward but can be a little confusing initially. 

First, create a file in your root directory called .env.local. This is a useful filename because its already in your gitignore file. This saves you the step of adding it there or the pain of possibly forgetting to add it entirely.

Second, create your react environment variable. Please note, they must start with REACT_APP like the following `REACT_APP_CLIENT_ID='8hafhafohaofhado1`'.

Finally, access it inside your React application by creating objects starting with `process.env`. So lets day we wanted to load a bunch of users inside a componentDidMount lifecycle method. To do so we would do something like the following:
```
  async componentDidMount() {
    const res = await axios.get(
      `https://api.github.com/users?client_id=${process.env.REACT_APP_CLIENT_ID}&client_secret=${process.env.REACT_APP_CLIENT_SECRET}`
    );
    this.setState({ users: res.data });
  }
```

