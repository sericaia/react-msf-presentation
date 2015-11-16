## react-router


Route > Component


A Component handles a Route


```js
let routes = (<Router>
  <Route component={App} path='/'>
    <Route component={About} path='about' />
  </Route>
</Router>);
```

### `DefaultRoute`

You always need one


```js
let routes = (<Router>
  <Route path='/' component={App}>
    <Route path='about' component={About} />
    <IndexRoute component={Home} />
  </Route>
</Router>);
```


### props.children

```js
class App extends React.Component {
  render() {
    return (<div>
      {this.props.children}
    </div>);
  }
};
```
```js
class Home extends React.Component {
  render() {
    return (<h1>Hello from `Home`</h1>);
  }
};
```
```js
let routes = (<Router>
  <Route path='/'component={App}>
    <Route path='about' component={About} />
    <IndexRoute component={Home}/>
  </Route>
</Router>);
```


### `NotFoundRoute`

```js
class NotFound extends React.Component {
  render() {
    return (<h1>Nothing to see here</h1>);
  }
};

let routes = (<Router>
  <Route path='/' component={App}>
    <Route path='about' component={About} />
    <IndexRoute component={Home} />
    <NotFoundRoute component={NotFound} />
  </Route>
</Router>);
```


### `run`

```js
React.render(routes, document.body);
```


### Locations

  * HistoryLocation > `/home`
  * HashLocation > `/#/home`


### `Link`

```js
<Link to='home'>Home</Link>
```
```js
<a href='/home'>Home</a>
```
```js
<a href='/home' className='active'>Home</a>
```


## Nested

[*snippet too big to show here*](https://gist.github.com/ramitos/bd15e67186ffae11d3a9)
