# Course Introduction and Overview

[Advance React on Scrimba](https://scrimba.com/learn/react/course-introduction-and-overview-cRqV4ktg)

![Screenshot 2022-12-19 at 3 54 54 PM](https://user-images.githubusercontent.com/89284873/208531578-415e1ef2-3f89-454a-8753-54f227ebb48f.png)

![Screenshot 2022-12-19 at 3 59 29 PM](https://user-images.githubusercontent.com/89284873/208532260-b08dc464-a594-48ec-b673-7157b00a7a1f.png)

# Setting the Stage with Modern JavaScript features

```js
import React, {Component} from "react"

class NewJSFeatures extends Component {
    constructor() {
        super()
        this.state = {
            count: 0
        }
        this.increment = this.increment.bind(this)
        this.decrement = this.decrement.bind(this)
    }
    
    increment() {
        this.setState(prevState => {
            return {
                count: prevState.count + 1
            }
        })
    }
    
    decrement() {
        this.setState(prevState => {
            return {
                count: prevState.count - 1
            }
        })
    }
    
    render() {
        return (
            <div>
                <h1>{this.state.count}</h1>
                <button onClick={this.increment}>+</button>
                <button onClick={this.decrement}>-</button>
            </div>    
        )
    }
}

export default NewJSFeatures
```

- we can now use arrow functions for our class methods
```js
    increment = () => {
        this.setState(prevState => {
            return {
                count: prevState.count + 1
            }
        })
    }
```

```js
decrement = () => {
        this.setState(prevState => {
            return {
                count: prevState.count - 1
            }
        })
}
```

- arrow functions have implicit return

```js
increment = () => {
        this.setState(prevState => ({count: prevState.count + 1}))
    }
```

- the ability to have class fields in our classes

```js
class NewJSFeatures extends Component {
    state = {
        count: 0
    }
```

- object destructuring

```js
 render() {
        const {count} = this.state
        return (
            <div>
                <h1>{count}</h1>
                <button onClick={this.increment}>+</button>
                <button onClick={this.decrement}>-</button>
            </div>    
        )
    }
}
```

## All changes

```js
import React, {Component} from "react"

class NewJSFeatures extends Component {
    state = {
        count: 0,
        greeting: "Hi",
        age: 42
    }
    
    increment = () => {
        this.setState(prevState => ({count: prevState.count + 1}))
    }
    
    decrement = () => {
        this.setState(prevState => {
            return {
                count: prevState.count - 1
            }
        })
    }
    
    render() {
        const {count: number, greeting, age} = this.state
        return (
            <div>
                <h1>{number}</h1>
                <button onClick={this.increment}>+</button>
                <button onClick={this.decrement}>-</button>
            </div>    
        )
    }
}

export default NewJSFeatures
```

![Screenshot 2022-12-19 at 4 13 10 PM](https://user-images.githubusercontent.com/89284873/208536833-92e6537b-4c36-4e25-9be3-8d2c0ac727af.png)
