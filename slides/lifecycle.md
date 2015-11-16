## Lifecycle


Hooking into the specific moments of the Component lifecycle


### Mounting


#### `componentWillMount`

Invoked once, immediately before the initial rendering occurs. You can mutate the state that it will be reflected when rendered for the first time


#### `componentDidMount`

Invoked once, **after** the being rendered for the first time and attached to the DOM.

Note: You can use `componentDidMount` to start logic in the component, like some asynchronous data fetching, timers, etc.


```js
class extends React.Component {
  componentWillMount() {
    console.log('component is going to render');
  }
  componentDidMount() {
    console.log('component just rendered');
  }
  render() {
    console.log('component is rendering');
    return (<h1>Heyo</h1>);
  }
};
```


### Updating


Component instances can live even after you create render them again with new properties

[(demo)](https://jsfiddle.net/xw6vgnkf/1/)

Note: If you run this example, you will see that "Anchor mounted" will only be logged once even though `App.render` is called multiple times rendering `Anchor` with different `props`.  However, if you hook into the `componentWillReceiveProps` event in `Anchor`.


```js
class Anchor extends React.Component {
  componentDidMount() {
    console.log('Anchor mounted');
  },
  componentWillReceiveProps() {
    console.log('Anchor is receiving new props');
  },
  render() {
    console.log('Anchor is rendering');
    return (<a href={this.props.href}>{this.props.href}</a>);
  }
};
```


```
Anchor mounted
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
Anchor is receiving new props
Anchor is rendering
...
```


React keeps track of each component instance


#### `componentWillReceiveProps`

Invoked when a component instance is updated with new props. It's not invoked for the initial `render`, you can mutate the state without triggering another render


#### `shouldComponentUpdate`

Invoked before re-rendering a component instance - either because it was updated or because the state was mutated with `setState`. With this method, you can decide whether it should render or not


#### `componentWillUpdate`

Invoked immediately before re-rendering. The state cannot be mutated using `setState` in this method


#### `componentDidUpdate`

Invoked immediately after the component was re-rendered and the DOM reflects the new view


### Unmounting


#### `componentWillUnmount`

Invoked immediately before a component instance is unmounted from the DOM. very useful to do some cleanup in your component, like cleaning timers, or cancelling async operations.


## Server vs Client

|                             | Server | Client |
| --------------------------- |:------:|:------:|
| `componentWillMount`        |    ✔   |    ✔   |
| `componentDidMount`         |    ✘   |    ✔   |
| `componentWillReceiveProps` |    ✔*  |    ✔   |
| `shouldComponentUpdate`     |    ✔*  |    ✔   |
| `componentWillUpdate`       |    ✔*  |    ✔   |
| `componentDidUpdate`        |    ✔*  |    ✔   |
| `componentWillUnmount`      |    ✔*  |    ✔   |


## Initial render

`componentWillMount` > `render` > `componentDidMount`


## Update

`shouldComponentUpdate` > `componentWillUpdate` > `render` > `componentDidUpdate`


![](https://pbs.twimg.com/media/B-G3_T8CcAAmTHV.jpg:large)


## EXERCICES
