# React

A JavaScript library for building user interfaces

- Declarative
- Component-based
- Learn once, write anywhere

Link: [React JS](https://reactjs.org)

## Table of Contents

- [A Simple Component](#a-simple-component)
- [A Stateful Component](#a-stateful-component)
- [An Application](#an-application)
- [A Component Using External Plugins](#a-component-using-external-plugins)

## A Simple Component

React components implement a render() method that takes input data and returns what to display.
This example uses an XML-like syntax called JSX. Input data that is passed into the component can be accessed by render() via this.props.

```js
class HelloMessage extends React.Component {
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}

root.render(<HelloMessage name="Taylor" />);
```

<img width="246" alt="Screen Shot 2022-10-04 at 8 41 29 PM" src="https://user-images.githubusercontent.com/89284873/193961199-13ac1834-ea00-46e9-a2bf-58ba83bb9ab4.png">

## A Stateful Component

In addition to taking input data (accessed via this.props), a component can maintain internal state data (accessed via this.state).
When a component’s state data changes, the rendered markup will be updated by re-invoking render().

```js
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  tick() {
    this.setState((state) => ({
      seconds: state.seconds + 1,
    }));
  }

  componentDidMount() {
    this.interval = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}

root.render(<Timer />);
```

<img width="247" alt="Screen Shot 2022-10-04 at 8 41 52 PM" src="https://user-images.githubusercontent.com/89284873/193961248-84309b2b-be36-4ef4-85c4-99db59c8077c.png">

## An Application

Using props and state, we can put together a small Todo application.
This example uses state to track the current list of items as well as the text that the user has entered.
Although event handlers appear to be rendered inline, they will be collected and implemented using event delegation.

```js
class TodoApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = { items: [], text: "" };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  render() {
    return (
      <div>
        <h3>TODO</h3>
        <TodoList items={this.state.items} />
        <form onSubmit={this.handleSubmit}>
          <label htmlFor="new-todo">What needs to be done?</label>
          <input
            id="new-todo"
            onChange={this.handleChange}
            value={this.state.text}
          />
          <button>Add #{this.state.items.length + 1}</button>
        </form>
      </div>
    );
  }

  handleChange(e) {
    this.setState({ text: e.target.value });
  }

  handleSubmit(e) {
    e.preventDefault();
    if (this.state.text.length === 0) {
      return;
    }
    const newItem = {
      text: this.state.text,
      id: Date.now(),
    };
    this.setState((state) => ({
      items: state.items.concat(newItem),
      text: "",
    }));
  }
}

class TodoList extends React.Component {
  render() {
    return (
      <ul>
        {this.props.items.map((item) => (
          <li key={item.id}>{item.text}</li>
        ))}
      </ul>
    );
  }
}

root.render(<TodoApp />);
```

<img width="241" alt="Screen Shot 2022-10-04 at 8 42 30 PM" src="https://user-images.githubusercontent.com/89284873/193961318-8f1f8969-c677-4251-8ad9-122fe598d040.png">

## A Component Using External Plugins

React allows you to interface with other libraries and frameworks.
This example uses remarkable, an external Markdown library, to convert the textarea’s value in real time.

```js
class MarkdownEditor extends React.Component {
  constructor(props) {
    super(props);
    this.md = new Remarkable();
    this.handleChange = this.handleChange.bind(this);
    this.state = { value: 'Hello, **world**!' };
  }

  handleChange(e) {
    this.setState({ value: e.target.value });
  }

  getRawMarkup() {
    return { __html: this.md.render(this.state.value) };
  }

```

<img width="244" alt="Screen Shot 2022-10-04 at 8 44 42 PM" src="https://user-images.githubusercontent.com/89284873/193961548-8714d735-9cc3-4bab-b3f4-dbacce3b231c.png">

## Resources

- [Babel](https://babeljs.io) - JavaScript Compiler

** Note: This is not the official documentation site anymore. Switching to beta. **
