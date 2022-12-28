# React's Tree Rendering

- we need to understand how react renders the component that it renders:

1. React recursively renders components down one branch until there are no more to render

  - We have the ` App ` component that's rendering a ` p ` and two ` GrandParent ` components

```js
import React, {Component} from "react"
import Child from "./Child"

class Parent extends Component {
    render() {
        console.log("[ ]   [👩🏼‍⚕️]   [ ]   [ ] rendered")
        return (
            <div>
                <p>I'm a Parent Component</p>
                <Child />
                <Child />
            </div>
        )
    }
}

export default Parent
```

  - ` GrandParent ` is rendering a ` p ` and two ` parent ` components

```js
import React, {Component} from "react"
import Parent from "./Parent"

class GrandParent extends Component {
    render() {
        console.log("[👴🏼]   [ ]   [ ]   [ ] rendered")
        return (
            <div>
                <p>I'm a GrandParent Component</p>
                <Parent />
                <Parent />
            </div>
        )
    }
}

export default GrandParent
```

  - the ` parent ` is rendering a ` p ` and two ` child ` components

```js
import React, {Component} from "react"
import Child from "./Child"

class Parent extends Component {
    render() {
        console.log("[ ]   [👩🏼‍⚕️]   [ ]   [ ] rendered")
        return (
            <div>
                <p>I'm a Parent Component</p>
                <Child />
                <Child />
            </div>
        )
    }
}

export default Parent
```

  - and the ` child ` is rendering a ` p ` and two ` GrandChild ` components

```js
import React, {Component} from "react"
import GrandChild from "./GrandChild"

class Child extends Component {
    render() {
        console.log("[ ]   [ ]   [🧒🏻]   [ ] rendered")
        return (
            <div>
                <p>I'm a Child Component</p>
                <GrandChild />
                <GrandChild />
            </div>
        )
    }
}

export default Child
```

- the point of this is just to create a strong hierarchy and see that as we get lower and lower there's gonna be a lot more instances of 
` GrandChild ` than it will ever be of ` Parents ` , there should be 16 of the ` GrandChild ` components.

- Diagram:

![Screenshot 2022-12-28 at 12 57 15 PM](https://user-images.githubusercontent.com/89284873/209859617-6908c47c-2401-4749-bd0f-bde73ffc4ebb.png)

2. Changes to state or props in any component will recursively re-render down the remaining tree whether those components have changed or not.

- Diagram:

![Screenshot 2022-12-28 at 12 58 36 PM](https://user-images.githubusercontent.com/89284873/209859729-449e5a8a-a4d8-4bf6-b372-0809d6720569.png)

![Screenshot 2022-12-28 at 12 58 51 PM](https://user-images.githubusercontent.com/89284873/209859746-d4f1c1bc-dc2b-44c8-8172-f5f9285d2dd9.png)

3. ` shouldComponentUpdate() ` method, ` React.PureComponent ` , and ` React.memo() ` are tools to help fix this problem. ⬆️

## Summary

- In React, the term "tree rendering" refers to the way that the React framework constructs and updates the user interface (UI) of an application.

- React uses a virtual DOM (a lightweight in-memory representation of the actual DOM) to render and update the UI of an application. When the state of a component changes, React will first create a new virtual DOM representation of the updated component. It will then compare this new virtual DOM representation to the previous one using a diffing algorithm, which determines the minimum number of DOM operations needed to update the actual DOM to match the new virtual DOM.

- This process is known as "tree rendering" because the virtual DOM can be thought of as a tree structure, with the root node representing the top-level component and each branch representing a nested component. When a component's state changes, React will update the virtual DOM tree by adding, removing, or modifying the nodes that represent that component and its descendants.

- Tree rendering is an important aspect of React's design because it allows the framework to efficiently update the UI in response to changes in the component state, without having to rebuild the entire UI from scratch each time. This makes it possible to build fast, responsive user interfaces that can handle frequent updates and updates.
