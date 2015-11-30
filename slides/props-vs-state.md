## Props vs State

```js
class Sum extends React.Component {
  constructor(props) {
    super(props);

    this.state = { sum: props.a + props.b };
  }
  render() {
    return (<p>
      {this.props.a} + {this.props.b} = {this.state.sum}
    </p>);
  }
};
```


* **`props`**: function parameters
* **`state`**: variables declared in the function scope

Note:
* **`props`** is kind of a public API that each component exposes;
* **`state`** is the internal and private values that a component needs to keep to  manage its logic.


|                                              | `props` | `state` |
| -------------------------------------------- |:-------:|:-------:|
| Can get initial value from parent component? |    ✔    |    ✘    |
| Can be updated by parent component?          |    ✔    |    ✘    |
| Should be mutated inside component?          |    ✘    |    ✔    |
