---
layout: post
title:      "Async & this.props"
date:       2019-07-07 06:39:30 +0000
permalink:  async_and_this_props
---

I ran into an interesting issue recently trying to get this.props to properly return and render. I thought I would include the abbreviated solution in case anyone ever encounters the same issue.

 Not Returning this.props.post.anyProperty

```
class Post extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      post: {}
    };}

  componentDidMount() {
    this.props.getPost(this.props.match.params.id);

  renderPost() {
    return (
      <div className="content">
        <h4 className="title">this.props.post.title</h4>
      </div>
    );}

  render() {
    return (
      <div className="content-top">
        <div>{this.renderPost()}</div>
      </div>
    );}}

const mapStateToProps = (state, ownProps) => {
  return { post: state.posts[ownProps.match.params.id] };
};

export default connect(
  mapStateToProps,
  { getPost })(Post);
```


SOLUTION

```
class Post extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      loaded: false,
      post: {}
    };
  }

  async componentDidMount() {
    await this.props.getPost(this.props.match.params.id);
    await this.setState({ loaded: true });
  }

  renderPost() {
    return (
      <div className="content">
        <h4 className="title">
          {this.props.post.title}
        </h4>
    );
  }

  render() {
    return (
      <div className="content-top">
        <div>{this.state.loaded && this.renderPost()}</div>
      </div>
    );
  }
}

const mapStateToProps = (state, ownProps) => {
  return { post: state.posts[ownProps.match.params.id] };
};

export default connect(
  mapStateToProps,
  { getPost }
)(Post);
```

