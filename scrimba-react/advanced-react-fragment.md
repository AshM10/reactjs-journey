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

# Default Props

- a fallback or a backup

```app.js
import React from "react"
import Card from "./Card"

function App() {
    return (
        <div>
            <Card cardColor="red" />
            <Card />
            <Card cardColor="green" />
        </div>
    )
}

export default App
```

```card.js
import React from "react"

function Card(props) {
    const styles = {
        backgroundColor: props.cardColor,
        height: 100,
        width: 100
    }
    
    return (
        <div style={styles}></div>
    )
}

export default Card
```

![Screenshot 2022-12-20 at 12 44 28 PM](https://user-images.githubusercontent.com/89284873/208742549-5fc0f193-cfa9-4d57-a141-4969b60990ce.png)

![Screenshot 2022-12-20 at 12 44 51 PM](https://user-images.githubusercontent.com/89284873/208742620-37a887ff-3d50-4602-b388-49d9695674fd.png)

- this is where default props come in

*lines 15-17*

```Card.js
import React from "react"

function Card(props) {
    const styles = {
        backgroundColor: props.cardColor,
        height: 100,
        width: 100
    }
    
    return (
        <div style={styles}></div>
    )
}

Card.defaultProps = {
    cardColor: "blue"
}

export default Card
```

## Challenge

<!-- Set height and weight default -->

[My Solution](https://scrimba.com/scrim/co5cf472a89c5eb21e0772063)

```App.js
import React from "react"
import Card from "./Card"

function App() {
    return (
        <div>
            <Card cardColor="red" height={200} width={400} />
            <Card />
            <Card cardColor="green" />
        </div>
    )
}

export default App
```

```Card.js
import React from "react"

function Card(props) {
    const styles = {
        backgroundColor: props.cardColor,
        height: props.height,
        width: props.width
    }
    
    return (
        <div style={styles}></div>
    )
}

Card.defaultProps = {
    cardColor: "blue",
    height: 100,
    width: 100
}

export default Card
```

- what does this look like in a class component?

```Card.js
import React from "react"

class Card extends React.Component {
    render() {
        const styles = {
            backgroundColor: this.props.cardColor,
            height: this.props.height,
            width: this.props.width
        }
        
        return (
            <div style={styles}></div>
        )
    }
}

Card.defaultProps = {
    cardColor: "blue",
    height: 100,
    width: 100
}

export default Card
```

- convert this to a static property

```js
import React from "react"

class Card extends React.Component {
    static defaultProps = {
        cardColor: "blue",
        height: 100,
        width: 100
    }
    
    render() {
        const styles = {
            backgroundColor: this.props.cardColor,
            height: this.props.height,
            width: this.props.width
        }
        
        return (
            <div style={styles}></div>
        )
    }
}

export default Card
```

# Prop Types

- another way to add validation to your components is to add some prop types
- it allows you to specify that the incoming props should be a data type
- add some type checking for the incoming props
- moved to a separate library called prop types

![Screenshot 2022-12-20 at 12 59 56 PM](https://user-images.githubusercontent.com/89284873/208745240-502d2ada-fe64-496f-859f-a19817919d06.png)

```
$ npm install prop-types
```

1. ``` import PropTypes from "prop-types" ```
2. specify the prop types

```js
Card.propTypes = {
    cardColor: PropTypes.string
}
```

- this will be helpful for you when you are developing
- we can also specify that a prop is required for a component

```js
Card.propTypes = {
    cardColor: PropTypes.string.isRequired
}
```

![Screenshot 2022-12-20 at 1 04 08 PM](https://user-images.githubusercontent.com/89284873/208746151-72c2b28d-bfc8-4a20-ba04-2198bc8b04b7.png)

[React Docs on PropTypes](https://reactjs.org/docs/typechecking-with-proptypes.html#proptypes)

## Challenge

// Challenge: Add prop types for the height and width. Make at least one of them required.
// Extra Challenge: Make it so your incoming cardColor is only valid if it is "blue" or "red".

[My Solution](https://scrimba.com/scrim/co369441c928d1a67a03b0c68)

// Make sure that card color is required again

[My Solution](https://scrimba.com/scrim/co77f48beaa0a310adfd48445)

- it is becoming more popular to write React with TypeScript, until then, it is better to include Prop Types
- it will make your app debugging much easier

```App.js
import React from "react"
import Card from "./Card"

function App() {
    return (
        <div>
            <Card cardColor="red" height={200} width={200} />
            <Card cardColor="purple" />
            <Card cardColor="green" />
        </div>
    )
}

export default App
```

```Card.js
import React from "react"
import PropTypes from "prop-types"

function Card(props) {
    const styles = {
        backgroundColor: props.cardColor,
        height: props.height,
        width: props.width
    }
    
    return (
        <div style={styles}></div>
    )
}

Card.propTypes = {
    cardColor: PropTypes.oneOf(["red", "blue", "green", "purple"]).isRequired,
    height: PropTypes.number.isRequired,
    width: PropTypes.number
}

Card.defaultProps = {
    height: 100,
    width: 100
}

export default Card
```

