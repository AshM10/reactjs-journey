# React Fragment

- the components you create can only return a single parent element
- if you need to return sibling elemnents, you need to wrap them in a parent element
- helps us wrap our elements that we are returning into something that does not create a new element or node in the DOM tree

```html
<html>
    <head>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div id="root"></div>
        <script src="index.pack.js"></script>
    </body>
</html>

<!-- <div id="root">
    <div>
        <div>
            <h1>I'm the Child component</h1>
            <div>
                <hr>
                <h3>I'm the Grandchild component</h3>
                <p>I'm also a part of the Grandchild component</p>
            </div>
        </div>
    </div>
</div> -->

<div id="root">
    <h1>I'm the Child component</h1>
    <hr>
    <h3>I'm the Grandchild component</h3>
    <p>I'm also a part of the Grandchild component</p>
</div>
```

```js
import React from "react"

function Grandchild() {
    return (
        <React.Fragment>
            <hr />
            <h3>I'm the Grandchild component</h3>
            <p>I'm also a part of the Grandchild component</p>
        </React.Fragment>
    )
}

export default Grandchild
```

- it does not just simplifies the tree, but it changes the relationship between these components. (parent and child relationships)
- be careful when you use React Fragment especially when you need a parent-child relationship in your layout. i.e grid or flex
- other ways of writing React Fragment

```js
import React, {Fragment} from "react"
import Child from "./Child"

function App() {
    return (
        <Fragment>
            <Child />
        </Fragment>
    )
}

export default App
```

```js
import React from "react"
import Child from "./Child"

function App() {
    return (
        <>
            <Child />
        </>
    )
}

export default App
```

