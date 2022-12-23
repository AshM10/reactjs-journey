# Render Props

- In React, a component's props (short for properties) are a way for the parent component to pass data to the child component. The child component can then access and use the data through the props object.
- Here's an example of how you might use props in a React component:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage(props) {
  return <h1>{props.message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes a message prop to the WelcomeMessage component
function App() {
  return <WelcomeMessage message="Hello World!" />;
}
```

- In the example above, the App component is the parent component and the WelcomeMessage component is the child component. The App component passes a prop called message to the WelcomeMessage component, which is then rendered in the component's JSX using {props.message}.
- You can also use props to pass functions as callbacks. For example:

```js
import React from 'react';

// This is a functional component that displays a button
// When the button is clicked, it calls a function passed in as a prop called "onClick"
function Button(props) {
  return <button onClick={props.onClick}>Click me</button>;
}

// This is the parent component that renders the Button component
// It passes an onClick prop to the Button component
function App() {
  const handleClick = () => {
    console.log('Button was clicked');
  };

  return <Button onClick={handleClick} />;
}
```

-In this example, the App component passes a function called handleClick to the Button component as a prop called onClick. When the button is clicked, the handleClick function is called.

## Callback functions

- the method we are calling allows it, or even expects is:

```js
document.getElementById("button").addEventListener("click", function() {
    console.log("Clicked!")
})

document.getElementById("input").addEventListener("input", function() {
    console.log("Input changed!")
})

document.getElementById("box").addEventListener("mouseover", function() {
    console.log("Hovered in box!")
})
```

https://user-images.githubusercontent.com/89284873/209394202-597b2c3c-7aea-4604-ad01-4fa370ad826e.png)](https://user-images.githubusercontent.com/89284873/209394360-ef8e9505-9b25-4b0c-b609-4b5a793df828.mov

- we can also add some parameters inside the function

```js
document.getElementById("button").addEventListener("click", function(event) {
    console.log(event)
})
```

- these are all the properties that will show up, one of the most useful is the target:

![Screenshot 2022-12-23 at 12 59 05 PM](https://user-images.githubusercontent.com/89284873/209394696-2c3c9975-2d13-44c2-8b45-d25eb006d1a7.png)

## Summary: Callback Function and Parameters

- A callback function is a function that is passed as an argument to another function and is executed after some kind of event. Callback functions are often used in JavaScript to perform a certain action after an event has occurred, such as a user clicking a button or a page loading.
- Here's an example of a callback function:

```js
function greet(name, callback) {
  console.log(`Hello, ${name}!`);
  callback();
}

function sayGoodbye() {
  console.log('Goodbye!');
}

greet('John', sayGoodbye);
```

- In this example, the greet function takes two arguments: a name and a callback function. The greet function logs a greeting to the console and then calls the callback function. The sayGoodbye function is passed as the callback argument to the greet function, and it logs a goodbye message to the console when it is called.
- When the code is run, it will log "Hello, John!" to the console and then "Goodbye!" to the console.
- A callback function can also accept parameters. For example:

```js
function greet(name, callback) {
  console.log(`Hello, ${name}!`);
  callback(name);
}

function sayGoodbye(name) {
  console.log(`Goodbye, ${name}!`);
}

greet('John', sayGoodbye);
```

- In this example, the sayGoodbye function accepts a name parameter and logs a goodbye message using the name parameter. When the code is run, it will log "Hello, John!" to the console and then "Goodbye, John!" to the console.

# Render Props Part 2

- To render props in a React component, you can access the props object in the component's render method or in the component's function body if it's a functional component.
- Here's an example of rendering props in a class-based React component:

```js
import React from 'react';

// This is a class-based component that displays a message
// The message is passed in as a prop called "message"
class WelcomeMessage extends React.Component {
  render() {
    return <h1>{this.props.message}</h1>;
  }
}

// This is the parent component that renders the WelcomeMessage component
// It passes a message prop to the WelcomeMessage component
class App extends React.Component {
  render() {
    return <WelcomeMessage message="Hello World!" />;
  }
}
```

- In the example above, the WelcomeMessage component is a class-based component that has a render method that returns JSX that includes the message prop. The App component is the parent component that renders the WelcomeMessage component and passes a message prop to it.
- Here's an example of rendering props in a functional component:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage(props) {
  return <h1>{props.message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes a message prop to the WelcomeMessage component
function App() {
  return <WelcomeMessage message="Hello World!" />;
}
```

- In the example above, the WelcomeMessage component is a functional component that takes in a props object as an argument and returns JSX that includes the message prop. The App component is the parent component that renders the WelcomeMessage component and passes a message prop to it.
- You can also use the destructuring syntax to make it easier to access props in a functional component:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage({ message }) {
  return <h1>{message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes a message prop to the WelcomeMessage component
function App() {
  return <WelcomeMessage message="Hello World!" />;
}
```

- In the example above, the WelcomeMessage component is a functional component that takes in a message prop as an argument and returns JSX that includes the message prop. The App component is the parent component that renders the WelcomeMessage component and passes a message prop to it.

- By now, you should be familiar with passing props into your own custom component:

*App.js*

```js
import React from "react"
import Example from "./Example"

function App() {
    return (
        <div>
            <Example name={"Bob"} />
        </div>
    )
}

export default App
```

*Example.js*

```js
import React from "react"

function Example(props) {
    return <h1>Hi {props.name}</h1>
}

export default Example
```

![Screenshot 2022-12-23 at 1 07 21 PM](https://user-images.githubusercontent.com/89284873/209395523-ba2c6e22-11af-483f-a893-dbb461bd8aea.png)

## Data types you can pass as props

- In React, you can pass any data type as a prop to a component. This includes:

1. Primitive data types: strings, numbers, booleans, and null
2. Complex data types: arrays, objects, and functions
3. JSX elements

- Here are some examples of passing different data types as props in a React component:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage(props) {
  return <h1>{props.message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes different types of props to the WelcomeMessage component
function App() {
  return (
    <div>
      <WelcomeMessage message="Hello World!" />
      <WelcomeMessage message={123} />
      <WelcomeMessage message={true} />
      <WelcomeMessage message={null} />
      <WelcomeMessage message={['a', 'b', 'c']} />
      <WelcomeMessage message={{ key: 'value' }} />
      <WelcomeMessage message={() => console.log('Hello!')} />
    </div>
  );
}
```

- In the example above, the App component passes different types of props to the WelcomeMessage component. These include a string, a number, a boolean, null, an array, an object, and a function.
- It's important to note that when passing an object or array as a prop, you should make sure to create a new instance of the object or array rather than modifying the original object or array. This is because React uses shallow comparison to determine if a prop has changed, and modifying the original object or array will not trigger a re-render of the component.
- For example, the following code will not trigger a re-render of the WelcomeMessage component because the original array is modified:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage(props) {
  return <h1>{props.message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes an array as a prop to the WelcomeMessage component
// and then modifies the original array
function App() {
  const array = ['a', 'b', 'c'];
  return (
    <div>
      <WelcomeMessage message={array} />
      <button onClick={() => array.push('d')}>Add element</button>
    </div>
  );
}
```

- To trigger a re-render of the WelcomeMessage component when the array is modified, you should create a new instance of the array:

```js
import React from 'react';

// This is a functional component that displays a message
// The message is passed in as a prop called "message"
function WelcomeMessage({ message }) {
  return <h1>{message}</h1>;
}

// This is the parent component that renders the WelcomeMessage component
// It passes an array as a prop to the WelcomeMessage component
// When the array is modified, it creates a new instance of the array
// and passes it as a prop to trigger a re-render of the WelcomeMessage component
class App extends React.Component {
  state = {
    data: ['a', 'b', 'c']
  };

  modifyArray = () => {
    this.setState({
      data: [...this.state.data, 'd']
    });
  };

  render() {
    return (
      <>
        <WelcomeMessage message={this.state.data} />
        <button onClick={this.modifyArray}>Modify array</button>
      </>
    );
  }
```

### Passing a function

*App.js*

```js
import React from "react"
import Example from "./Example"

function App() {
    return (
        <div>
            <Example render={
                function(isDaytime) {
                    return (
                        <h1>{isDaytime ? "Good day" : "Good evening"}, Bob!</h1>
                    )
                }
            }/>
        </div>
    )
}

export default App
```

*Example.js*

```js
import React from "react"

function Example(props) {
    return (
        <div>
            {props.render(true)}
        </div>
    )
}

export default Example
```

## Challenge

- make the function receives a number and renders something based on that number

[My Solution](https://scrimba.com/scrim/co6004b608d82d7bc4bfb3c29)

```js
import React from "react"

function Example(props) {
    return (
        <div>
            {props.render(-42)}
        </div>
    )
}

export default Example
```

```
import React from "react"
import Example from "./Example"

function App() {
    return (
        <div>
            <Example render={
                function(number) {
                    return (
                        <h1>{number >=0 ? "Positive" : "Negative"}</h1>
                    )
                }
            }/>
        </div>
    )
}

export default App
```

![Screenshot 2022-12-23 at 1 26 39 PM](https://user-images.githubusercontent.com/89284873/209397211-2de3ed79-802c-4137-9e9b-58a1df416acb.png)

### What is render() in react?

- In React, the render() method is a lifecycle method that is called automatically by the React framework. It is used to render the content of a React component to the DOM (Document Object Model).
- The render() method is responsible for producing a tree of React elements that represent the component's visual output. It is called each time the component's state or props (short for "properties") change, and the output is updated to reflect the new state or props.
- Here is an example of a simple render() method in a React component:

```js
render() {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>This is a simple React component.</p>
    </div>
  );
}
```

- This render() method returns a single React element, which is a div element that contains an h1 element and a p element. When this component is rendered, it will produce the following HTML:

```html
<div>
  <h1>Hello, World!</h1>
  <p>This is a simple React component.</p>
</div>
```

- The render() method is the most important method in a React component, as it determines what the component will actually render to the screen. It is called automatically by the React framework, and you should not call it directly. Instead, you should focus on writing the logic that goes inside the render() method to define the component's output.

## Challenge

- pass and render an array or object

*Example.js*

```js
import React from "react"

function Example(props) {
    return (
        <div>
            {props.render(true, 42)}
        </div>
    )
}

export default Example
```

*App.js*

```js
import React from "react"
import Example from "./Example"

function App() {
    return (
        <div>
            <Example render={
                function(bool, number) {
                    return (
                        <div>
                            <h1>{number}</h1>
                            <h1>{bool ? "true" : "false"}</h1>
                        </div>
                    )
                }
            }/>
        </div>
    )
}

export default App
```

![Screenshot 2022-12-23 at 1 34 44 PM](https://user-images.githubusercontent.com/89284873/209398691-7c7b6884-25d6-4b9d-ac98-09a673fff89f.png)

### Passing an array as a prop

- To pass an array as a prop in a React component, you can include it as an attribute in the JSX element that represents the component. -  - Here's an example of how you might do this:

```js
import React from 'react';

// define an array of data that you want to pass as a prop
const myArray = [1, 2, 3, 4, 5];

// define a component that takes an array as a prop
function MyComponent(props) {
  return (
    <div>
      {props.myArray.map(item => (
        <div key={item}>{item}</div>
      ))}
    </div>
  );
}

// render the component and pass the array as a prop
render(
  <MyComponent myArray={myArray} />,
  document.getElementById('root')
);
```

- In this example, the MyComponent component is defined to take an array as a prop called myArray. The component then uses the map function to render a list of items from the array. When the component is rendered, the myArray prop is passed to it, and the component can use the data from the array to render its content.
- It's also possible to pass an array as a prop using the spread operator. For example:

```js
render(
  <MyComponent {...{myArray}} />,
  document.getElementById('root')
);
```

- This will pass the entire myArray object as a prop to the MyComponent component.

*If you have to chooses between HOCs and render props, choose render props*

### Refactoring HOC to render props

- In React, a Higher Order Component (HOC) is a function that takes a component and returns a new component. HOCs are a way to reuse code, render high-level abstractions, and manipulate the behavior of a component.
- One way to refactor an HOC to use the "render props" pattern is to pass a function as a prop to the HOC, and then have the HOC call that function with the desired data or behavior as an argument.
- Here's an example of an HOC that adds a loading indicator to a component:

```js
const withLoadingIndicator = WrappedComponent => {
  return class extends React.Component {
    render() {
      return this.props.isLoading ? (
        <div>Loading...</div>
      ) : (
        <WrappedComponent {...this.props} />
      );
    }
  };
};
```

- To refactor this HOC to use the render props pattern, we can pass a function as a prop to the HOC, and then have the HOC call that function with the desired data or behavior as an argument.
- Here's the refactored HOC:

```js
const withLoadingIndicator = render => {
  return class extends React.Component {
    render() {
      return this.props.isLoading ? (
        render({ isLoading: true })
      ) : (
        render({ isLoading: false })
      );
    }
  };
};
```

- To use this HOC, you would pass a function as the render prop to the HOC, and then use the data or behavior provided by the HOC in the function body:

```js
const MyComponent = () => (
  <div>
    <withLoadingIndicator
      render={({ isLoading }) => (isLoading ? <div>Loading...</div> : <div>Loaded</div>)}
    />
  </div>
);
```

- This pattern is called "render props" because the prop passed to the HOC is a function that is used to render the component. It is a way to share behavior between components without using inheritance or HOCs.

## Refactoring our HOC sample to render props

- Delete the HOC folder

![Screenshot 2022-12-23 at 1 55 31 PM](https://user-images.githubusercontent.com/89284873/209400454-8bbe687e-a533-4fe2-bc57-db975eaadda4.png)

*Toggler.js*

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
        return (
            <div>
                {this.props.render(this.state.on, this.toggle)}
            </div>
        )
    }
}

export default Toggler
```

*Favorite.js*

```js
import React, {Component} from "react"
import Toggler from "./Toggler"

function Favorite(props) {
    return (
        <Toggler render={function(on, toggle) {
            return (
                <div>
                    <h3>Click heart to favorite</h3>
                    <h1>
                        <span 
                            onClick={toggle}
                        >
                            {on ? "❤️" : "♡"}
                        </span>
                    </h1>
                </div>
            )
        }}/>
    ) 
}

export default Favorite
```

- we oftentimes use the arrow function with the implicit return like this:

*Favorite.js*

```js
import React, {Component} from "react"
import Toggler from "./Toggler"

function Favorite(props) {
    return (
        <Toggler render={
            (on, toggle) => (
                <div>
                    <h3>Click heart to favorite</h3>
                    <h1>
                        <span 
                            onClick={toggle}
                        >
                            {on ? "❤️" : "♡"}
                        </span>
                    </h1>
                </div>
            )
        }/>
    ) 
}

export default Favorite
```

## Challenge

// bring in the Toggler component
// render the Toggler inside the Menu, and use the render prop to determine what will get displayed
// remember to bring in the "goodies" (state and methods) to that function so you can make this work

[My Solution](https://scrimba.com/scrim/cocf64ad1acbf0e872eea4bc1)

```js
import React from "react"
import Toggler from "./Toggler"
// render the Toggler inside the Menu, and use the render prop to determine what will get displayed
// remember to bring in the "goodies" (state and methods) to that function so you can make this work

function Menu(props) {
    return (
        <Toggler render={(on, toggle) => (
            <div>
                <button onClick={toggle}>{on ? "Hide" : "Show"} Menu </button>
                <nav style={{display: on ? "block" : "none"}}>
                    <h6>Signed in as Coder123</h6>
                    <p><a>Your Profile</a></p>
                    <p><a>Your Repositories</a></p>
                    <p><a>Your Stars</a></p>
                    <p><a>Your Gists</a></p>
                </nav>
            </div>
        )}/>
    ) 
}

export default Menu
```

## Set the default value

*Toggler.js*

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
        console.log(this.state.on)
        return (
            <div>
                {this.props.render(this.state.on, this.toggle)}
            </div>
        )
    }
}

Toggler.defaultProps = {
    defaultOnValue: false
}

export default Toggler
```

- you can also write the default on static

```js
import React, {Component} from "react"

class Toggler extends Component {
    state = {
        on: this.props.defaultOnValue
    }
    
    static defaultProps = {
        defaultOnValue: false
    }
    
    toggle = () => {
        this.setState(prevState => {
            return {
                on: !prevState.on
            }
        })
    }
    
    render() {
        console.log(this.state.on)
        return (
            <div>
                {this.props.render(this.state.on, this.toggle)}
            </div>
        )
    }
}

export default Toggler
```

*Menu.js*

```js
import React from "react"
import Toggler from "./Toggler"
// render the Toggler inside the Menu, and use the render prop to determine what will get displayed
// remember to bring in the "goodies" (state and methods) to that function so you can make this work

function Menu(props) {
    return (
        <Toggler defaultOnValue={true} render={(on, toggle) => (
            <div>
                <button onClick={toggle}>{on ? "Hide" : "Show"} Menu </button>
                <nav style={{display: on ? "block" : "none"}}>
                    <h6>Signed in as Coder123</h6>
                    <p><a>Your Profile</a></p>
                    <p><a>Your Repositories</a></p>
                    <p><a>Your Stars</a></p>
                    <p><a>Your Gists</a></p>
                </nav>
            </div>
        )}/>
    ) 
}

export default Menu
```

*Favorite.js*

```js
import React, {Component} from "react"
import Toggler from "./Toggler"

function Favorite(props) {
    return (
        <Toggler render={
            (on, toggle) => (
                <div>
                    <h3>Click heart to favorite</h3>
                    <h1>
                        <span 
                            onClick={toggle}
                        >
                            {on ? "❤️" : "♡"}
                        </span>
                    </h1>
                </div>
            )
        }/>
    ) 
}

export default Favorite
```

## Passing a single parameter instead of two

```js
render() {
        return (
            <div>
                {this.props.render({
                    on: this.state.on, 
                    toggle: this.toggle
                })}
            </div>
        )
    }
```

``` Toggler defaultOnValue={true} render={({on, toggle}) ```

``` ({on, toggle}) ```

## Wrapping the Menu inside the Toggler

*App.js*

```js
import React from "react"
import Menu from "./Menu"
import Favorite from "./Favorite"
import Toggler from "./Toggler"

function App() {
    return (
        <div>
            <Toggler defaultOnValue={true} render={({on, toggle}) => {
                return (
                    <Menu on={on} toggle={toggle}/>
                )
            }}/>
            <hr />
            <Favorite />
        </div>
    )
}

export default App
```

*Menu.js*

```js
import React from "react"
import Toggler from "./Toggler"
// render the Toggler inside the Menu, and use the render prop to determine what will get displayed
// remember to bring in the "goodies" (state and methods) to that function so you can make this work

function Menu(props) {
    return (
        <div>
            <button onClick={props.toggle}>{props.on ? "Hide" : "Show"} Menu </button>
            <nav style={{display: props.on ? "block" : "none"}}>
                <h6>Signed in as Coder123</h6>
                <p><a>Your Profile</a></p>
                <p><a>Your Repositories</a></p>
                <p><a>Your Stars</a></p>
                <p><a>Your Gists</a></p>
            </nav>
        </div>
    ) 
}

export default Menu
```

