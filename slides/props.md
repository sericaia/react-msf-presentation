## Props

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.href}>link</a>);
  }
}
```

```js
React.render(<Anchor href='http://yld.io' />, document.body);
```


Using interpolation:

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


### Types

Unlike `HTML` you can use any variable type in the attributes


#### Object

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.opts.href}>link</a>);
  }
}
```

```js
let opts = {
  href: 'http://yld.io'
};

<Anchor opts={opts} />
```


#### String

*as seen before*

```js
class Anchor extends React.Component {
  render() {
    return (<a href={this.props.opts.href}>link</a>);
  }
}
```

```js
let yldAddress = 'http://yld.io';
<Anchor href={yldAddress} />
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


#### Boolean

```js
class Anchor extends React.Component {
  render() {
    let shouldLinkToBlog = this.props.shouldLinkToBlog;
    let href = shouldLinkToBlog ? 'http://blog.yld.io' : 'http://yld.io'
    return (<a href={href}>link</a>);
  }
}
```

```js
let shouldLinkToBlog = false;
<Anchor blogLink={shouldLinkToBlog} />
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

Is going to generate:
```js
<a href='blog.yld.io' target='_blank' />
```


### `propTypes`

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


**Only checked on developer mode**


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

```
<a href='http://yld.io' target='_blank'>b</a>
```


### Imutability

`this.props` should **NEVER** be updated.


### EXERCISE