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


`React.initializeTouchEvents(true)`

Note: because if you support touch events you'll when you click you need to wait to see if its a touch and hold


### Component <-> Component

Note: comunication between components


```js
class Anchor extends React.Component {
  onClick() {
    this.props.onHey('HEY');
  }
  render() {
    return (<button onClick={this.onClick.bind(this)}>Build an "Hey"</button>);
  }
};
```
```js
class Anchor extends React.Component {
  gotHey(msg) {
    window.alert(msg);
  },
  render() {
    return (<HeyMachine onHey={this.gotHey.bind(this)} />);
  }
};
```

Note: As you can see in this example, `HeyMachine` expects to receive an `onHey` property. That property should be a function. Then, it listens to the `onClick` event from the `<button>`. When an user clicks on the `<button>`, `HeyMachine.onClick` is invoked. There, `HeyMachine` invokes `this.props.onHey` that happens to be `App.gotHey`.


Great way for components to communicate with each other


Variation of the **callback pattern** that you learned in Node.js


## EXERCICE