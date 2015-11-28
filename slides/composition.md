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
class Phone extends React.Component {
  render() {
    return (
      <li>{this.props.type} developed by {this.props.provider}</li>
    );
  }
};
```
```js
class App extends React.Component {
  render() {
    return (
      <div>
        <ul>
          <Phone type='Windows Phone' provider='Microsoft' />
          <Phone type='Android' provider='Google' />
          <Phone type='iOS' provider='Apple' />
        <ul>
    </div>);
  }
};
```

Note: we are reducing the code we need to write because we are reusing the Phone component


```js
var phoneList = [{
  type: 'Windows Phone',
  provider: 'Microsoft'
}, {
  /* ... */
}];
```
```js
class App extends React.Component {
  render() {
    let tags = [];
    for (let i in phoneList) {
      tags[i] = (<Phone type={phoneList[i].type}
                        provider={phoneList[i].provider} />);
    }

    return (<div>{tags}</div>);
  }
};
```

Note: we can make it better by programatically generate the `Phone` instances


```js
var phoneList = [{
  type: 'Windows Phone',
  provider: 'Microsoft'
}, {
  /* ... */
}];
```
```js
class App extends React.Component {
  render() {
    let tags = phoneList.map(function(phone) {
      return (<Phone type={phoneList[i].type}
                     provider={phoneList[i].provider} />);
    });

    return (<div>{tags}</div>);
  }
};
```

Note: Now with a map we don't even need to manage the loop


```js
class App extends React.Component {
  render() {
    return (<div>{phoneList.map(function(phone) {
      return (<Phone type={phoneList[i].type}
                     provider={phoneList[i].provider} />);
    })}</div>);
  }
};
```

Note: We can inline expressions in jsx


## DEMO
Composition - Cutlery
