# Section intro and Figma file

Learning how to use data in creating our web pages. 

## Data-driven React 

Data-driven React refers to a method of building React applications where the components are primarily driven by the data that is passed to them. This means that the behavior and rendering of the components is determined by the data they receive, rather than hard-coded logic. This approach allows for more dynamic and flexible applications, as the components can easily adapt to different data sets and scenarios.

## What we'll learn

![Screenshot 2023-01-13 at 1 25 16 PM](https://user-images.githubusercontent.com/89284873/212402045-ffd4e75a-4bdb-4b87-8432-066dfe713547.png)

In React, props (short for "properties") are a way to pass data from a parent component to a child component. They are passed to the child component as an object, and the child component can then access the props using the `this.props` object.

For example, consider a parent component that renders a list of items:

```js
class ParentComponent extends React.Component {
  render() {
    const items = ['item 1', 'item 2', 'item 3'];
    return (
      <div>
        {items.map(item => <ChildComponent item={item} />)}
      </div>
    );
  }
}
```

n this example, `ParentComponent` renders a `ChildComponent` for each item in the `items` array, and it passes each item as a prop called `item`. The child component can then access the `item` prop like this:

```js
class ChildComponent extends React.Component {
  render() {
    return <div>{this.props.item}</div>;
  }
}
```

In this way, we can create multiple instances of a component and pass different data to them using props, which can be create using an array.


## Airbnb Clone Project Setup

Link to my project repo: [React Airbnb Clone](https://github.com/AshM10/airbnb-clone)
