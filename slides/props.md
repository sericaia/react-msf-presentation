## Props

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href}>link</a>);
  }
}
```

```js
let yldAddress = 'http://yld.io';
<Anchor href={yldAddress} />
```

<!-- Using Types :: Unlike `HTML` you can use any variable type in the attributes -->
<!-- We could pass strings, booleans, objects, functions... -->


#### Object

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.myObj.href}>link</a>);
  }
}
```

```js
let myObj = {
  href: 'http://yld.io'
};

<Anchor myObj={myObj} />
```


#### Function

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href()}>link</a>);
  }
}
```

```js
let yldAddress = () => {
  return 'http://yld.io';
};
<Anchor href={yldAddress} />
```


### `this.props.children`

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href}>{this.props.children}</a>);
  }
}
```

```js
<Anchor href='http://yld.io'/><span>YLD!</span></Anchor>
```

`this.props.children == <span>YLD!</span>`


```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href}>{this.props.children}</a>);
  }
}
```

```js
<Anchor href='http://yld.io'/>YLD!</Anchor>
```

`this.props.children == 'YLD!'`


### `defaultProps`

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href} target={this.props.target} />);
  }
}

Anchor.defaultProps = {
  href: 'http://yld.io',
  target: '_blank'
};
```

```js
<Anchor href='blog.yld.io'/>
```

V
```js
<a href='blog.yld.io' target='_blank' />
```


### `propTypes (Validation)`
<!-- **Only checked on developer mode** -->
```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href} target={this.props.target} />);
  }
};

Anchor.defaultProps = {
  target: '_blank'
};

Anchor.propTypes = {
  href: React.PropTypes.string.isRequired,
  target: React.PropTypes.string,
};
```

```js
<Anchor />
```

```
Warning:
Failed propType: Required prop `href` was not specified in `Anchor`.
```


### ES6 spread operator

```js
class Anchor extends React.Component {
  render() {
    let {href, target} = this.props;
    return (<a href={href} target={target} />);
  }
};
```

```js
var props = {
  href: 'http://yld.io',
  target: '_blank'
};

<Anchor {...props} />
```
Is going to generate:
```
<a href='http://yld.io' target='_blank' />
```


### Imutability

`this.props` should **NEVER** be updated.


### DEMO
properties
