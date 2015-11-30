## Composition Patterns
* Container Components
* Smart and Dumb Components


## Container Components

> "A container does data fetching and then renders its corresponding sub-component."

<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source: https://medium.com/@learnreact/container-components-c0e67432e005</a>


```js
// CommentList.js
class CommentList extends React.Component {
  constructor() {
    super();
    this.state = { comments: [] }
  }
  componentDidMount() {
    $.ajax({
      url: "/my-comments.json",
      dataType: 'json',
      success: function(comments) {
        this.setState({comments: comments});
      }.bind(this)
    });
  }
  render() {
    return <ul> {this.state.comments.map(function(comment) {
      <li>{comment}</li>
    })} </ul>;
  }
}
```
<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source:  https://medium.com/@learnreact/container-components-c0e67432e005</a>

Note:
- This component is responsible for both fetching data and presenting it.
- There’s nothing “wrong” with this but you miss out on a few benefits of React.


## Disadvantages of this approach
- (less) Reusability
- (less) Data structure

<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source: https://medium.com/@learnreact/container-components-c0e67432e005</a>

Note:
- 1 This component can just be used if the conditions are the same (e.g endpoint change)
- 2 Misses state expectations of the required data (e.g PropTypes validation)


### Alternative - CommentListContainer
```js
// CommentListContainer.js
class CommentListContainer extends React.Component {
  constructor() {
    super();
    this.state = { comments: [] }
  }
  componentDidMount() {
    $.ajax({
      url: "/my-comments.json",
      dataType: 'json',
      success: function(comments) {
        this.setState({comments: comments});
      }.bind(this)
    });
  }
  render() {
    return <CommentList comments={this.state.comments} />;
  }
}
```

<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source: https://medium.com/@learnreact/container-components-c0e67432e005</a>

Note: data-fetching into a container component


### Alternative - CommentList
```js
// CommentList.js
class CommentList extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <ul> {this.state.comments.map(function(comment) {
      <li>{comment}</li>
    })} </ul>;
  }
}
```
<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source: https://medium.com/@learnreact/container-components-c0e67432e005</a>

Note: CommentList receive comments has a property


## Advantages
* **Separation of concerns** - data fetching and rendering
* CommentList is now **reusable**
<!-- * CommentList could not have PropTypes **validation** -->

<a href="https://medium.com/@learnreact/container-components-c0e67432e005" class="refs">Source: https://medium.com/@learnreact/container-components-c0e67432e005</a>


## Smart and Dumb Components


## Smart and Dumb Components

|                             | Dumb      | Smart     |
| --------------------------- |:---------:|:---------:|
| `Dependencies`              |    ✘      |    ✔      |
| `Receive data via props`    |    ✔      |    ✔*     |
| `Own CSS file`              |    ✔      |    ✘      |
| `Own state`                 |    ✘      |    ✔      |
| `Example`                   | UserInfo  | UserPage  |

Note:
Dumb: 1) Allow to access to this.props.children; 2) Might use other dumb components.

Smart:
1. Wrap one or more dumb or smart components.
2. Hold state (from Flux stores) and pass it as objects to dumb components.
3. Dont use DOM directly (use dumb components for layout)


## Benefits of This Approach
* Separation of concerns
* Reusability
* Dumb components without app logic
* Identify layouts and avoid duplication

Note:
1. more organization
2. use same dumb component with different state sources
3. designers don't need to be concerned about logic
4. layout component - e.g navigation menu


## Dumb vs Smart conclusion
> Components don’t have to emit DOM. They only need to provide composition boundaries between UI concerns.

<a href="https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0" class="refs">Source: https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0</a>
