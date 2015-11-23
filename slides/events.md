## Events


Listen an act on DOM events


```js
class Anchor extends React.Component {
  onClick(ev) {
    console.log('user clicked on the <a>');
    console.log(ev);
  }
  render() {
    return (<a onClick={this.onClick.bind(this)}>link</a>);
  }
};
```


[more supported events](https://facebook.github.io/react/docs/events.html)


### Component <-> Component

Note: communication between components


```js
class HelloFactory extends React.Component {
  onClick() {
    this.props.onHello('Hello, Webcamp!');
  }
  render() {
    return (
      <button onClick={this.onClick.bind(this)}>
        Build an "Hello"
      </button>
    );
  }
};
```
```js
class Anchor extends React.Component {
  gotHello(msg) {
    window.alert(msg);
  },
  render() {
    return (<HelloFactory onHello={this.gotHello.bind(this)} />);
  }
};
```

Note: As you can see in this example, `HelloFactory` expects to receive an `onHello` property. That property should be a function. Then, it listens to the `onClick` event from the `<button>`. When an user clicks on the `<button>`, `HelloFactory.onClick` is invoked. There, `HelloFactory` invokes `this.props.onHello` that happens to be `App.gotHello`.


Great way for components to communicate with each other


## DEMO
