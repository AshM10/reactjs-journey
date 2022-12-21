# Code Reuse in React

- a really important aspect in being a React developer is understanding the methods and design patterns that have emerged as React has matured
- similar goal: avoid Repetition

## DRY

- Don't Repeat Yourself
- more room for human error, more room for bugs

- Inheritance is what drives OOP, includes classes, subsclasses, inheriting traits from superclasses and so forth
- Composition is a way to compose your code structure by pulling together the bits and pieces you need

## Which one should we use when creating our React applications?

-You should always prefer COMPOSITION over INHERITANCE in React: [Composition Over Inheritance](https://www.youtube.com/watch?v=wfMtDGfHWpA)

![Screenshot 2022-12-21 at 3 11 18 PM](https://user-images.githubusercontent.com/89284873/209003419-a1a67ec5-e28f-4272-9e20-395a8f7abe58.png)

- [React Documentation](https://reactjs.org/docs/composition-vs-inheritance.html#so-what-about-inheritance)

1. Components with props - you can use your component all over your app anytime you need it, pass props and render them differently depending on which props you pass to them
2. Children
3. Higher-order Components
4. Render props

*When React introduced HOOKS, both Higher-order Components and Render props became outdated.*

# React Children

- a good way to introduce reusability:

```js
import React from "react"

function App() {
    return (
        <div>
            <Navbar backgroundColor="firebrick" />
            <Button backgroundColor="blue" text="Click me!"/>
        </div>
    )
}

export default App
```

*providing a different prop and allow that to be customizable*

- example of a call to action component that will highlight a certain part of the page with a border

```js
import React from "react"

function CTA() {
    return (
        <div className="border">
            <h1>This is an important CTA</h1>
            <button>Click me now or you'll miss out!</button>
        </div>
    )
}

export default CTA
```

![Screenshot 2022-12-21 at 3 22 36 PM](https://user-images.githubusercontent.com/89284873/209004948-beeef9e5-3c5b-4e77-bfca-3b3180b02a0d.png)

this is where children come in to play, any component that you make can be used as a self-closing element, it can also be used in a non self-closing function and anything you put in between will be automatically accessible inside of that component via a prop called props.children

```App.js
import React from "react"
import CTA from "./CTA"

function App() {
    return (
        <div>
            <CTA>
                <h1>This is an important CTA</h1>
                <button>Click me now or you'll miss out!</button>
            </CTA>
        </div>
    )
}

export default App
```

```CTA.js
import React from "react"

function CTA(props) {
    return (
        <div className="border">
            {props.children}
        </div>
    )
}

export default CTA
```

*specify where you want the children to be put in this CTA.js component*
*this is specially useful when you want all your i.e pop-up boxes to look the same*

```css
.border {
    border: 1px solid blue;
    border-radius: 5px;
    padding: 10px;
}
```

```js
import React from "react"

function CTA(props) {
    return (
        <div className="border">
            {props.children}
        </div>
    )
}

export default CTA
```

```js
import React from "react"
import CTA from "./CTA"

function App() {
    return (
        <div>
            <CTA>
                <h1>This is an important CTA</h1>
                <button>Click me now or you'll miss out!</button>
            </CTA>
            
            <CTA>
                <form>
                    <input type="email" placeholder="Enter email address here"/>
                    <br />
                    <button>Submit</button>
                </form>
            </CTA>
        </div>
    )
}

export default App
```

![Screenshot 2022-12-21 at 3 29 26 PM](https://user-images.githubusercontent.com/89284873/209005906-f8d98e74-04c7-47b0-b5f5-817cbfe3a09a.png)

- You can still put in props

```js
<CTA position="right">
    <h1>This is an important CTA</h1>
    <button>Click me now or you'll miss out!</button>
</CTA>
```       

- do not use the children property too often, passing simple data, a component with props is the best way to go
- if you want to ensure a certain structure always, just use props

## Challenge: React Children

// implement a regular Callout component that can take children instead of having the three separte components having their own children in them

[My Solution](https://scrimba.com/scrim/co77f405b9285b3ce8d84de47)

![Screenshot 2022-12-21 at 3 47 09 PM](https://user-images.githubusercontent.com/89284873/209008302-bff0700b-baef-4bd2-b4ac-b771610d14b4.png)

```Callout.js
import React from "react"

function Callout(props) {
    return (
        <div className="callout">
            {props.children}
        </div>
    )
}

export default Callout
```

```App.js
import React from "react"
import Callout from "./Callout"

function App() {
    return (
        <main>
            <h1>Welcome!</h1>
            
            <Callout>
                <h2>Don't miss out!</h2>
                <p>Unless you don't suffer from FOMO, you better make sure you fill out the email form below!</p>
            </Callout>
            
            <p>This is probably the best site you've ever come across. I'm glad you're here to witness the magnificence of this website right now.</p>
            
            <Callout>
                <img src="https://picsum.photos/id/102/4320/3240" width="100%" />
                <figcaption>Just look at those sparkling raspberries!</figcaption>
            </Callout>
            
            <p>Here's some more unforgettable content. Lorem ipsum something or other.</p>
            
            <Callout>
                <h2>Give us your email. We definitely won't sell it to anyone.</h2>
                <input type="email" placeholder="Enter Email"/>
                <button>Sign me up!</button>
            </Callout>
            
        </main>
    )
}

export default App
```

# Higher Order Components (HOCs)

- stems from the concepts of higher order functions: just a function that takes another function as a parameter i.e callbacks, .map(), .filter(), .reduce()
-  a function that takes a component as its first arguments and returns a new component that wraps the given component, providing extra capabilities to it: a function that takes a component and supercharges it

![Screenshot 2022-12-21 at 3 54 19 PM](https://user-images.githubusercontent.com/89284873/209009273-a292c85f-0c47-40c2-8fc3-e703ae5e55ec.png)

*this is not very DRY, so we will see how HOCs can help us fix this problem*

- basic HOCs syntax: 

```js
const upgradedComponent = withSuperPowers(Component)
export default upgradedComponent
```

```js
const componentWithToggle = withToggle(Component)
export default componentWithToggle
```

*you don't usually see it written in two lines, this is just for learning*

- usually you'll see it like this:

``` export default withToggle(Component) ```

![Screenshot 2022-12-21 at 3 59 01 PM](https://user-images.githubusercontent.com/89284873/209010235-5e03aa37-3f68-475c-9d5d-a1bbd3cb9f47.png)

```js
import React from "react"

// A function that takes a component as its first argument and returns a new component that wraps the given component, providing extra capabilities to it.

export function withPointlessHOC(component) {
    const Component = component
    return function(props) {
        return (
            <Component {...props} />
        )
    }
}
```

*in your App,js, replace the export default App with:*

```
import React from "react"
import {withPointlessHOC} from "./withPointlessHOC"

function App(props) {
    return (
        <div>Hello world!</div>
    )
}

const PointlessHOC = withPointlessHOC(App)
export default PointlessHOC
```

- HOC function has the ability to pass any component that you invoke it with and has the ability to augment the props

*withExtraPropAdded.js*

```js
import React from "react"

export function withExtraPropAdded(component) {
    const Component = component
    return function(props) {
        return (
            <Component anotherProp="Blah blah blah" {...props} />
        )
    }
}
```

*App.js*

```js
import React from "react"
import {withPointlessHOC} from "./withPointlessHOC"
import {withExtraPropAdded} from "./withExtraPropAdded"

function App(props) {
    console.log(props)
    return (
        <div>Hello world!</div>
    )
}

const ExtraPropComponent = withExtraPropAdded(App)
export default ExtraPropComponent
```

![Screenshot 2022-12-21 at 4 09 34 PM](https://user-images.githubusercontent.com/89284873/209011691-a3f39b3c-b744-41be-b219-8b1ff1b44289.png)

## Challenge: Higher Order Components (HOCs)

/**
 * A function that takes a component as its first argument and returns a new component that wraps
 * the given component, providing extra capabilities to it.
 * 
 * Challenge: Write a higher-order component that passes a new prop to the given component
 * called "favoriteNumber" and includes your own, personal, favorite number
 * 
 * Then, in App.js, render that favorite number to the screen
 */
 
 [My Solution](https://scrimba.com/scrim/cod824b38b095ea2500cec9d0)
 
 ```js
 import React from "react"
/**
 * A function that takes a component as its first argument and returns a new component that wraps
 * the given component, providing extra capabilities to it.
 * 
 * Challenge: Write a higher-order component that passes a new prop to the given component
 * called "favoriteNumber" and includes your own, personal, favorite number
 * 
 * Then, in App.js, render that favorite number to the screen
 */
export function withFavoriteNumber(component) {
    const C = component
    return function(props) {
        return (
            <C favoriteNumber={42} {...props}/>
        )
    }
}
```

```
import React from "react"
import {withFavoriteNumber} from "./withFavoriteNumber"

function App(props) {
    return (
        <div>{props.favoriteNumber}</div>
    )
}

export default withFavoriteNumber(App)
```

![Screenshot 2022-12-21 at 4 29 53 PM](https://user-images.githubusercontent.com/89284873/209014670-23f562f0-078a-44cc-b720-5bc7abc4eb94.png)

- best way to do this is

*index.js*

```js
import React from "react"
import ReactDOM from "react-dom"
import App from "./App"

ReactDOM.render(<App favoriteNumber={42} />, document.getElementById("root"))
```

