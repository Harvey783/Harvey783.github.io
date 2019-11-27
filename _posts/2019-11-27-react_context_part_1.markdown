---
layout: post
title:      "React Context Part 1"
date:       2019-11-27 12:09:58 +0000
permalink:  react_context_part_1
---


React's Context API is an alternative to Redux for application state management. It can be a little confusing to setup at first so I'm going to show what’s needed initially. Subsequent posts will build on this with the end result being a fully functional app using Context to manage state. Below is's super basic App.js file that simply searches for Github users.

```
import React, { Component, Fragment } from 'react';
import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';
import Navbar from './Components/Navbar';
import Users from './Components/Users';
import Search from './Components/Search';
import axios from 'axios';

class App extends Component {
  state = {
    users: []
  };

  searchUsers = async text => {
    const response = await axios.get(
      `https://api.github.com/search/users?q=${text}&client_id=${xxx}&client_secret=${xxx}`
    );
    this.setState({ users: response.data.items });
  };

  render() {
    return (
      <GitState>
        <Router>
          <Navbar />
          <Switch>
            <Route
              exact
              path="/"
              render={props => (
                <Fragment>
                  <Search searchUsers={this.searchUsers} />
                  <Users users={this.state.users} />
                </Fragment>
              )}
            />
          </Switch>
        </Router>
      </GitState>
    );
  }
}

export default App;
```

Now to set up Context you need to create three files inside a Context folder in your src directory. 

**Types.js**

Contains variables of strings that can be called to change state within a reducer. 
`export const SEARCH_USERS = 'SEARCH_USERS';`

**GitContext.js**

Need to initialize Context. Here we're initializing GitContext with createContext.
```
import {createContext} from 'react';
const GitContext = createContext()
export default GitContext;
```

**GitState.js**

Responsible for initializing state and includes any related actions such as our request to search for users. The useReducer hook is needed to dispatch to the reducer. GitContext.Provider contains everything we want available and props.children will make it accessible to the entire application.
```
import React, {useReducr} from 'react';
import GitContext from './GitContext';
import GitReducer from './GitReducer';
import {SEARCH_USERS} from './Types';

const GitState = props => {
  const initialState = {
  users: []
  }
	
  const [state,dispatch] = useReducr(GitReducer, initialState)

  return <GitContext.Provider 
  value={{
    users: state.users
  }}
  >
    {props.children}
  </GitContext.Provider>
}

export default GitState
```

The final thing to do now is import GitState into App.js, and make everything avaialble by wrapping your return The final thing to do now is import GitState into App.js and make everything available by wrapping your return statement like below. 
```
  render() {
    return (
      <GitState>
        <Router>
          <Navbar />
          <Switch>
            <Route
              exact
              path="/"
              render={props => (
                <Fragment>
                  <Search searchUsers={this.searchUsers} />
                  <Users users={this.state.users} />
                </Fragment>
              )}
            />
          </Switch>
        </Router>
      </GitState>
    );
  }
}
```
