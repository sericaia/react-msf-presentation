## Composition


**Use components to form components**


Reduce code duplication

✔


Create multiple layers of abstraction in your views

✔


Share code not only inside the same project, but also between different projects

✔


Encapsulate logic

✔


```js
class Alert extends React.Component {
  render() {
    var classNames = [
      'alert',
      'alert-' + this.props.type,
      'alert-dismissible'
    ].join(' ');

    return (<div className={classNames}>
      <span>{this.props.msg}</span>
    </div>);
  }
};
```
```js
class App extends React.Component {
  render() {
    return (<div>
      <Alert type='info' msg='Is this going to work?' />
      <Alert type='success' msg='Well done!' />
    </div>)
  }
};
```

Note: we are reducing the code we need to write because we are reusing the Alert component


```js
var alerts = [{
  type: 'info',
  msg: 'Is this going to work?'
}, {
  type: 'success',
  msg: 'Well done!'
}];
```
```js
class App extends React.Component {
  render() {
    let tags = [];
    for (let i in alerts) {
      tags[i] = (<Alert type={alerts[i].type} msg={alerts[i].msg} />);
    }

    return (<div>{tags}</div>);
  }
};
```

Note: we can make it better by programatically generate the `Alert` instances


```js
var alerts = [{
  type: 'info',
  msg: 'Is this going to work?'
}, {
  type: 'success',
  msg: 'Well done!'
}];
```
```js
class App extends React.Component {
  render() {
    let tags = alerts.map(function(alert) {
      return (<Alert type={alert.type} msg={alert.msg} />);
    });

    return (<div>{tags}</div>);
  }
};
```

Note: Now with a map we don't even need to manage the loop


```js
var alerts = [{
  type: 'info',
  msg: 'Is this going to work?'
}, {
  type: 'success',
  msg: 'Well done!'
}];
```
```js
class App extends React.Component {
  render() {
    return (<div>{alerts.map(function(alert) {
      return (<Alert type={alert.type} msg={alert.msg} />);
    })}</div>);
  }
};
```

Note: We can inline expressions in jsx


## EXERCICE