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

