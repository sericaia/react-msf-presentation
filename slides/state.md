## State


### State could be mutable


```js
class Checkbox extends React.Component {
  constructor() {
    super();

    this.state = {
      checked: false
    };
  }
  render() {
    return (<input type='checkbox' checked={this.state.checked} />);
  }
};
```


## `setState`

```js
class Checkbox extends React.Component {
  constructor() {
    super();

    this.state = { checked: false };

    setInterval(() => {
      this.setState({
        checked: !this.state.checked
      });
    }, 500);
  }
  render() {
    return (<input type='checkbox' checked={this.state.checked} />);
  }
};
```


![](https://cldup.com/0bulfjuJx0.gif)


`setState` triggers a re-render.

**It's the *only* thing in your component that can trigger an update to the view**


## DEMO
State - Lamp

![Image](https://media0.giphy.com/media/ame1y0MJNqUPC/200.gif)

<a href="https://media0.giphy.com/media/ame1y0MJNqUPC/200.gif" class="refs">GIF Source: https://media0.giphy.com/media/ame1y0MJNqUPC/200.gif</a>
