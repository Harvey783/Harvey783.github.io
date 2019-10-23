---
layout: post
title:      "React Inline Styling"
date:       2019-10-23 08:17:26 +0000
permalink:  react_inline_styling
---


Any element in React can be styled inline. Divs, navs, spans whatever you like. Unlike standard CSS, React's inline stlying requires two things. 1) To be enclosed in double brackets, and 2) For th CSS property to be in Camel-Case. So a React render method with inline styling would look this:

```
  render() {
    const { login, avatar_url, html_url } = this.state;
    return (
      <div className="card text-center">
        <img
          src={avatar_url}
          alt=""
          style={{ width: '70px', borderRadius: '75%' }}
        />
        <h4>
          <a href={html_url}>{login}</a>
        </h4>
      </div>
    );
  }
```
