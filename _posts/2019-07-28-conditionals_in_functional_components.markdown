---
layout: post
title:      "Conditionals in Functional Components"
date:       2019-07-28 18:57:56 +0000
permalink:  conditionals_in_functional_components
---


Ternary operators are a quick and easy way to implement a conditional in a functional component. Lets say you wanted to display a comment form depending on whether a user is signed-in. Inside the return statement of your functional component you could do something like the following:

```
<aside className="comment-lists-aside-section">
	{auth.isAuthenticated ? (
		<CommentForm postId={post._id} />
	) : (
		<CommentFormBlank/>
	)}
</aside>
```

Here, isAuthenticated is a boolean value with an initial state of false that becomes true upn sign-in. So when a user is logged-in you can display one of two components: the comment form or an empty component CommentFormBlank.
