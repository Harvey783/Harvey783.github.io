---
layout: post
title:      "Be Kind to Your API"
date:       2019-07-18 17:43:10 +0000
permalink:  be_kind_to_your_api
---


When setting up your useEffect hook in React try not to make the same mistake I always do by drowning the API in requests. Forgetting to include an empty array at the end of your useEffect hook results in an infinite request-loop that makes APIs so angry they totally stop listening to you. Its not personal. You only exceeded their maximum request limit, and no longer have access to their data. APIs really are surprisingly  lazy. Anyway, just make sure to include an array at the end of useEffect like below and you wont have to worry about getting the silent treatment from an API.

```
function App() {
  const [data, setData] = useState({ posts: [] });
  const [keyword, setKeyword] = useState('hooks');

  useEffect(() => {
    const fetchPosts = async () => {
      const response = await axios(
        `http://api.reddit.com/r/search?q=${keyword}`,
      );

      setData(response.data);
    };

    fetchPosts();
  }, [keyword]);// <------- DON'T FORGET

  return (
    <Fragment>
      // Way more stuff here
    </Fragment>
  );
}

export default App
```
