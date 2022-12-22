# Higher Order Components (HOCs) Part 3

*App.js*

```js
import React from "react"
import Menu from "./Menu"
import Favorite from "./Favorite"

function App() {
    return (
        <div>
            <Menu />
            <hr />
            <Favorite />
        </div>
    )
}

export default App
```

*Favorite.js*

```js
import React, {Component} from "react"

class Favorite extends Component {
    state = {
        isFavorited: false
    }
    
    toggleFavorite = () => {
        this.setState(prevState => {
            return {
                isFavorited: !prevState.isFavorited
            }
        })
    }
    
    render() {
        return (
            <div>
                <h3>Click heart to favorite</h3>
                <h1>
                    <span 
                        onClick={this.toggleFavorite}
                    >
                        {this.state.isFavorited ? "❤️" : "♡"}
                    </span>
                </h1>
            </div>
        ) 
    }
}

export default Favorite
```

*Menu.js*

```js
import React, {Component} from "react"

class Menu extends Component {
    state = {
        show: true
    }
    
    toggleShow = () => {
        this.setState(prevState => {
            return {
                show: !prevState.show
            }
        })
    }
    
    render() {
        return (
            <div>
                <button onClick={this.toggleShow}>{this.state.show ? "Hide" : "Show"} Menu </button>
                <nav style={{display: this.state.show ? "block" : "none"}}>
                    <h6>Signed in as Coder123</h6>
                    <a>Your Profile</a>
                    <a>Your Repositories</a>
                    <a>Your Stars</a>
                    <a>Your Gists</a>
                </nav>
            </div>
        ) 
    }
}

export default Menu
```

![Screenshot 2022-12-22 at 11 58 47 AM](https://user-images.githubusercontent.com/89284873/209197088-84b4d6d2-c10a-4b08-95d7-f0369137605a.png)
![Screenshot 2022-12-22 at 11 59 20 AM](https://user-images.githubusercontent.com/89284873/209197172-6311e96b-9538-4679-a5ba-496fa41ea7d6.png)

- Separating these inta HOC can be highly confusing so let's walk through it slowly:

1. Create a folder for the HOCs

![Screenshot 2022-12-22 at 12 01 51 PM](https://user-images.githubusercontent.com/89284873/209197544-5521f880-fd70-4ee5-98fb-51d3c95e3971.png)

![Screenshot 2022-12-22 at 12 02 20 PM](https://user-images.githubusercontent.com/89284873/209197615-0b2dc6be-550b-4841-8039-314fd6218fa8.png)

```js
import React from "react"

export function withToggler(component) {
    return function(props) {
        return (
            <Toggler />
        )
    }
}
```

2. import the function in the file where you want to use it

*Favorite.js*

```js
import React, {Component} from "react"
import {withToggler} from "./HOCs/withToggler"
```

3. How to use the withToggler function

- put it in front of Favorite: ``` export default withToggler(Favorite)

```js
import React, {Component} from "react"
import {withToggler} from "./HOCs/withToggler"

class Favorite extends Component {
    state = {
        isFavorited: false
    }
    
    toggleFavorite = () => {
        this.setState(prevState => {
            return {
                isFavorited: !prevState.isFavorited
            }
        })
    }
    
    render() {
        return (
            <div>
                <h3>Click heart to favorite</h3>
                <h1>
                    <span 
                        onClick={this.toggleFavorite}
                    >
                        {this.state.isFavorited ? "❤️" : "♡"}
                    </span>
                </h1>
            </div>
        ) 
    }
}


export default withToggler(Favorite)
```

Or you can make a variable for the new fav component

```js
const SuperChargedFavoriteComponent = withToggler(Function)
export default SuperChargedFavoriteComponent
```

- what you are actually exporting from Favorite.js is not the Favorite component that you wrote, but the beefed up version of the Favorite component

** Challenge

- import the withToggler in Menu.js

[My Solution](https://scrimba.com/scrim/co4c644b1ab9a3a3448409f3e)

```js
import React, {Component} from "react"
import {withToggler} from "./HOCs/withToggler"
class Menu extends Component {
    state = {
        show: true
    }
    
    toggleShow = () => {
        this.setState(prevState => {
            return {
                show: !prevState.show
            }
        })
    }
    
    render() {
        return (
            <div>
                <button onClick={this.toggleShow}>{this.state.show ? "Hide" : "Show"} Menu </button>
                <nav style={{display: this.state.show ? "block" : "none"}}>
                    <h6>Signed in as Coder123</h6>
                    <a>Your Profile</a>
                    <a>Your Repositories</a>
                    <a>Your Stars</a>
                    <a>Your Gists</a>
                </nav>
            </div>
        ) 
    }
}

export default withToggler(Menu)
```

4. Passing component down to Toggler via props

```js
import React from "react"

export function withToggler(component) {
    return function(props) {
        return (
            <Toggler component={component} {...props}/>
        )
    }
}
```

- this toggler component is going to hold all the functionality and state that our two Favorite and Menu conponents right now are duplicating
- we can start a state with class

```js
import React, {Component} from "react"

class Toggler extends Component {
    state = {
        on: false
    }
    
    toggle = () => {
        this.setState(prevState => {
            return {
                on: !prevState.on
            }
        })
    }
    
    render() {
        const Component = this.props.component
        return (
            <Component on={this.state.on} toggle={this.toggle} {...this.props} />
        )
    }
}

export function withToggler(component) {
    return function(props) {
        return (
            <Toggler component={component} {...props}/>
        )
    }
}
```

*Favorite.js*

```js
import React, {Component} from "react"
import {withToggler} from "./HOCs/withToggler"

class Favorite extends Component {
    render() {
        return (
            <div>
                <h3>Click heart to favorite</h3>
                <h1>
                    <span 
                        onClick={this.props.toggle}
                    >
                        {this.props.on ? "❤️" : "♡"}
                    </span>
                </h1>
            </div>
        ) 
    }
}

const SuperchargedFavoriteComponent = withToggler(Favorite)
export default SuperchargedFavoriteComponent
```

## Challenge

- Update the Menu component to simplify it

[My Solution](https://scrimba.com/scrim/coebf4510ad1e8d1af18c72cc)

```js
import React, {Component} from "react"
import {withToggler} from "./HOCs/withToggler"
class Menu extends Component {
    render() {
        return (
            <div>
                <button onClick={this.props.toggle}>{this.props.on ? "Hide" : "Show"} Menu </button>
                <nav style={{display: this.props.on ? "block" : "none"}}>
                    <h6>Signed in as Coder123</h6>
                    <a>Your Profile</a>
                    <a>Your Repositories</a>
                    <a>Your Stars</a>
                    <a>Your Gists</a>
                </nav>
            </div>
        ) 
    }
}

export default withToggler(Menu)
```

## Challenge

-Change the Menu class component to a basic functional component

[My Solution](https://scrimba.com/scrim/co3d841b1b17bbae52e346fb2)

```js
import React from "react"
import {withToggler} from "./HOCs/withToggler"

function Menu(props) {
    return (
        <div>
            <button onClick={props.toggle}>{props.on ? "Hide" : "Show"} Menu </button>
            <nav style={{display: props.on ? "block" : "none"}}>
                <h6>Signed in as Coder123</h6>
                <a>Your Profile</a>
                <a>Your Repositories</a>
                <a>Your Stars</a>
                <a>Your Gists</a>
            </nav>
        </div>
    ) 
}

export default withToggler(Menu)
```

- allowing other options

```js
import React, {Component} from "react"

class Toggler extends Component {
    state = {
        on: this.props.defaultOnValue
    }
    
    toggle = () => {
        this.setState(prevState => {
            return {
                on: !prevState.on
            }
        })
    }
    
    render() {
        const Component = this.props.component
        return (
            <Component on={this.state.on} toggle={this.toggle} {...this.props} />
        )
    }
}

export function withToggler(component, optionsObj) {
    return function(props) {
        return (
            <Toggler component={component} defaultOnValue={optionsObj.defaultOnValue} {...props}/>
        )
    }
}
```

*Favorite.js*

```js
const SuperchargedFavoriteComponent = withToggler(Favorite, {defaultOnValue: false})
export default SuperchargedFavoriteComponent
```

*Menu.js*

``` export default withToggler(Menu, {defaultOnValue: true}) ```

## Recap

- original problem: Both Favorite and Menu components are implementing their own logic and essentially did the same thing
- goal is reusability by making a withToggler and add it to our component and be able to supercharge our component
- withToggler takes a component and instead of rendering that component immediately, it renders our own custom component toggler, and then so toggler can eventually render the component we want to render and pass that component down to toggler
- and then our toggler component maintains the state and the ability to update the state and then  it finally renders the component that we pass down to it
- but instead of just rendering the component as a plain component it beefs it up with an on prop and a toggle prop and then of course passes any other props down so they don't get lost 
- while we're passing the rest of the props down, we can actually use the spread operator to pull some things out

*instead of*

```js
import React, {Component} from "react"

class Toggler extends Component {
    state = {
        on: this.props.defaultOnValue
    }
    
    toggle = () => {
        this.setState(prevState => {
            return {
                on: !prevState.on
            }
        })
    }
    
    render() {
        const Component = this.props.component
        return (
            <Component on={this.state.on} toggle={this.toggle} {...this.props} />
        )
    }
}

export function withToggler(component, optionsObj) {
    return function(props) {
        return (
            <Toggler component={component} defaultOnValue={optionsObj.defaultOnValue} {...props}/>
        )
    }
}
```

*we can do*

```js
import React, {Component} from "react"

class Toggler extends Component {
    state = {
        on: this.props.defaultOnValue
    }
    
    toggle = () => {
        this.setState(prevState => {
            return {
                on: !prevState.on
            }
        })
    }
    
    render() {
        const Component = this.props.component
        const {component: Component, defaultOnValue, ...props} = this.props
        return (
            <Component on={this.state.on} toggle={this.toggle} {...props} />
        )
    }
}

export function withToggler(component, optionsObj) {
    return function(props) {
        return (
            <Toggler component={component} defaultOnValue={optionsObj.defaultOnValue} {...props}/>
        )
    }
}
```

