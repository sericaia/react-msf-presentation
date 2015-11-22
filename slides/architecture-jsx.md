## React Architecture and JSX


## What is React?

View in MVC


## "JavaScript library for building user interfaces"


## React is fast due to its architecture


## < Add architecture image />


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


## React.Component
```js
class PartyInfo extends React.Component {};
```

#### Component Class
* Base class to create a react component using ES6
* Implements a render() function


## JSX with arguments
```js
class Hello extends React.Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
};
```

## Plain JS with element arguments
```js
class Hello extends React.Component {
  render() {
    return React.DOM.div(null, "Hello, ", this.props.name);
  }
};
```


## What is generated?
```js
class HelloWorld extends React.Component {
  render() {
    return (<h1>Hello World</h1>);
  }
};

React.render(<HelloWorld/>, document.getElementById('container'));
```
V
```html
<div id="container">
  <h1>Hello World</h1>
</div>
```


```js
/* ReactComponent render(ReactElement element,
    DOMElement container, [function callback]) */
React.render(<HelloWorld/>, document.getElementById('container'));
```
**React.render()** controls the contents of the container node you pass in. Any existing DOM elements inside are replaced when first called.

<!--
```js
class HelloWorld extends React.Component {      
  render() {
    return (React.createElement("h1", null, "Hello World"));
  }
};

React.render(React.createElement(HelloWorld, null),
    document.getElementById('container'));
```
ReactElement createElement(string/class type, [object props], [children ...]) -->


## Demo
Webcamp Component
<!-- how to create a component with es5 and es6 -->
