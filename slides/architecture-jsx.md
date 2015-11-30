## React Architecture and JSX


## What is React?

#### View in MVC


## JavaScript library for building user interfaces

Note: What is React?!
 - created by facebook
 - library, not framework


## React is fast due to its architecture

Note: Instead of having observables through the objects that we want to modify (as other frameworks do), React updates the DOM based on which objects the programmer allows to have notifiers.


## Architecture
![Image](./slides/images/architecture.png)

Note: virtual-DOM is the one that is manipulated (not the DOM) and a comparison is made


## It seems awesome, how can I install it?

* Using React from npm

```js
var React = require('react');
var ReactDOM = require('react-dom');
```


## React uses JSX syntax
```js
class PartyInfo extends React.Component {
  render() {
    return (
      <div>
        We are going to have a party!        
      </div>
    );
  }
};
```

Note: - we are not used to this (controller and html in the same file)
- similar to XML
- what we are used to do in views
- in the end, a transformation is done to turn JSX into JavaScript function calls


### React uses JSX syntax,
## but you don't need to use it


## Plain JavaScript
```js
class PartyInfo extends React.Component {
  render() {
    return React.DOM.div(null, "We are going to have a party!");
  }
};
```

Note: - first argument === null because there are no attributes in this div
- second argument = content
- third and so on - properties...


## React.Component
```js
class PartyInfo extends React.Component {};
```

#### Component Class
* Base class to create a react component using ES6
* Implements a render() function

Note: - Create a instance of a react component with the rendering


## JSX with arguments
```js
class Hello extends React.Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
};
```

Note: if we want to pass the name of the person, in JSX we will have something like this...


## Plain JS with element arguments
```js
class Hello extends React.Component {
  render() {
    return React.DOM.div(null, "Hello, ", this.props.name);
  }
};
```

Note: Using plain JavaScript, we need to add another argument to our div function. React will take care of this and will concatenate everything.


## What is generated?
```js
class HelloWorld extends React.Component {
  render() {
    return (<h1>Hello World</h1>);
  }
};

ReactDOM.render(<HelloWorld/>, document.getElementById('container'));
```
V
```html
<div id="container">
  <h1>Hello World</h1>
</div>
```

Note: ReactDOM.render() does not modify the container node (only modifies the children of the container).

<!--
```js
class HelloWorld extends React.Component {      
  render() {
    return (React.createElement("h1", null, "Hello World"));
  }
};

ReactDOM.render(React.createElement(HelloWorld, null),
    document.getElementById('container'));
```
ReactElement createElement(string/class type, [object props], [children ...]) -->


## Demo
Webcamp Component
<!-- how to create a component with es5 and es6 -->
