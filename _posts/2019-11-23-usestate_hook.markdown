---
layout: post
title:      "useState Hook"
date:       2019-11-23 19:44:08 -0500
permalink:  usestate_hook
---


Hooks are functions that let us hook into react state and lifecycle features from a functional component A common hook is useState, which allows one to use state inside a functional component. 

Lets say you had the following class component.

```
import React from 'react';

class Search extends React.Component {
  state = { text: ' ' };

  onChange = event => this.setState({ [event.target.name]: event.target.value });

  onSubmit = event => {
    event.preventDefault();
      this.props.searchUsers(this.state.text);
      this.setState({ text: '' });
  };

  render() {
    return (
      <div>
        <form onSubmit={this.onSubmit}>
          <input
            type="text"
            name="text"
            placeholder="Search for Users"
            value={this.state.text}
            onChange={this.onChange}
          />
          <input type="submit" value="Search" />
        </form>
      </div>
    );
  }
}

export default Search;
```

How would you convert this into a functioal component using the useState hook? First properly import useState. Next change the component from a class to a function by converting to an arrow function, adding destructured 'props' parameters, and removing the render statement. Then define state by destructuring it, adding an associated method(setText), and assigning it to the useState hook. Finally, add const before all methods, remove all this.state and this.props, and substiute setText for setState. The end result is below. 

```
import React, {( searchUsers)} from 'react';

const Search = props => {
  const [text, setText] = useState('');

  const onChange = event => setText(event.target.value);

  const onSubmit = event => {
    event.preventDefault();
      searchUsers(text);
      setText('');
  };

  return (
    <div>
      <form onSubmit={onSubmit}>
        <input
          type="text"
          name="text"
          placeholder="Search for Users"
          value={text}
          onChange={onChange}
        />
        <input type="submit" value="Search" />
      </form>
    </div>
  );
};

export default Search;
```
