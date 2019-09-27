---
layout: post
title:      "Controlled Inputs"
date:       2019-09-27 00:52:24 +0000
permalink:  controlled_inputs
---



When it comes to handling user input in React one way is by using a Controlled Input. The term ‘controlled’ is used because you control or manage the state directly by passing in a value, and keeping that value updated. A controlled component would look something like thus:

```
class ControlledInput extends React.Component {
  state = { text: '' };

  handleChange = event => {
    this.setState({
      text: event.target.value
    });
  };

  render() {
    return (
      <input type="text" 
      value={this.state.text} 
      onChange={this.handleChange} />
    );
  }
}

export default ControlledInput
```

Lets say a user has typed ‘Goodby’. The controlled input would work like this. A user types ‘e’ calling the onChange prop. onChange then calls handleChange. State updates  to ‘Goodbye’ and a re-render is triggered by setState.

