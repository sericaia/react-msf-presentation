## Lifecycle

Note: Hooking into the specific moments of the Component lifecycle


### Mounting


<p class="lifecycle-header">componentWillMount</p>

* Invoked once, immediately **before** the initial rendering occurs

Note: You can **mutate the state** that it will be reflected when rendered for the **first time**


<p class="lifecycle-header">componentDidMount</p>

* Invoked once, **after** the being rendered for the first time and attached to the DOM

Note: You can use `componentDidMount` to start logic in the component, like some asynchronous **data fetching, timers**, etc.


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
    return (<h1>Hello, Webcamp!</h1>);
  }
};
```


## DEMO
* Mounting and Unmounting


### Updating


Component instances can live even after you render them again with new properties


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


<p class="lifecycle-header">componentWillReceiveProps</p>

* Invoked when a component instance is updated with new props
* Not invoked in the initial `render`

Note: here you can mutate the state without triggering another render


<p class="lifecycle-header">shouldComponentUpdate</p>

* Before re-rendering a component instance
* Should the component render or not?

Note: 1- either because it was updated (props or state) or because the state was mutated with `setState`.
* shouldComponentUpdate: function(nextProps, nextState)


<p class="lifecycle-header">componentWillUpdate</p>

* Immediately before re-rendering
* The state cannot be mutated using `setState` in this method


<p class="lifecycle-header">componentDidUpdate</p>

* Immediately after the component was re-rendered and the DOM reflects the new view


### Unmounting


<p class="lifecycle-header">componentWillUnmount</p>

* Immediately before a component instance is unmounted from the DOM.
* Useful to cleanup

Note: 2 - like cleaning timers, or cancel async operations.


## Lifecycle Summary


## Initial render

`componentWillMount`

V

`render`

V

`componentDidMount`


## Update

`shouldComponentUpdate`

V

`componentWillUpdate`

V

`render`

V

`componentDidUpdate`
<!-- ![](https://pbs.twimg.com/media/B-G3_T8CcAAmTHV.jpg:large) -->


## DEMO
* Update

Note: Mounting/Unmounting Demo - If you run this example, you will see that "Anchor mounted" will only be logged once even though `App.render` is called multiple times rendering `Anchor` with different `props`.  However, if you hook into the `componentWillReceiveProps` event in `Anchor`.
