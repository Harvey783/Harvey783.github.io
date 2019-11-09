---
layout: post
title:      "onChange for Multiple Inputs"
date:       2019-11-09 23:14:25 +0000
permalink:  onchange_for_multiple_inputs
---


Lets say you needed an onChange method for the basic Search Component below. 

```
class Search extends React.Component {
  state = {
    text: ''
  };

  render() {
    return (
      <div>
        <form>
          <input
            type="text"
            name="text"
            placeholder="Search Here"
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

You could have an onChange method like below, which updates state specifically for the input named text.
```
  onChange = event => {
    this.setState({ text: event.target.value });
  };
```

Or you could have an onChange like below, which can handle multiple inputs because the more general input property 'name' is used instead. 
```
  onChange = event => {
    this.setState({ [event.target.name]: event.target.value });
  };
```
