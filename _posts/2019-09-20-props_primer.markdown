---
layout: post
title:      "Props Primer"
date:       2019-09-21 02:56:19 +0000
permalink:  props_primer
---


Props, short for properties, basically let you customize a component. They’re similar to function arguments in that sense.
```
// Function Arguements
greeting = (firstName, lastName) => {
  'Hello ' + firstName + ' ' + lastName;
};

// Component Props
<Student 
  age={35} 
  name={firstName + ' ' + lastName} 
/>;
```

Props are passed as the argument to a component function
```
const Hello = props => {
  <div>Hello, {props.name}</div>;
};
```

And thanks to ES6 they can be destructured
```
const Hello = props => {
  const { name } = props;
  return <div>Hello, {name}</div>;
};
```

One important thing to remember is that props are read-only, and can only be passed down to a child component. So how does a child component communicate something up to a parent component? By having the parent send down a function as a prop.
```
handleAction = event => {
  console.log('Child did:', event);
};

Parent = () => {
  return <Child onAction={handleAction} />;
};
```

The Child component receives the onAction prop, which it can call whenever it needs to send up data or notify the parent that something happened. One place where it’s common to pass functions as props is for even handling. The button below for example accepts an onClick prop, which it’ll call when the button is clicked.
```
Child = ({ onAction }) => {
  return <button onClick={onAction} />;
};
```

