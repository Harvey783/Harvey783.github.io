---
layout: post
title:      "Axios HTTP Requests"
date:       2019-11-04 03:22:31 +0000
permalink:  axios_http_requests
---


Axios is a populat HTTP Request middleware package that makes communicating with APIs quite easy. To use it first install it in your package.json file via `npm install axios --save`. Next, find an API, which IN this case will be Github. From there its pretty simple. For example you can do either a promise request or an async/await request like below.

Promise

```
class App extends Component {
  componentDidMount() {
    axios
      .get('https://api.github.com/users')
      .then(response => console.log(response.data));
   }
	}
```
	
	Async/Await
	
```
class App extends Component {
  async componentDidMount() {
	  const response = await axios.get('https://api.github.com/users');
	  console.log(response.data);
  }
}
```
	
