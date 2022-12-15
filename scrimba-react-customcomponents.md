# Custom Components

- allows us to write some code that we can execute over and over again just by calling that function
![Screenshot 2022-12-15 at 2 18 42 PM](https://user-images.githubusercontent.com/89284873/207958623-9c436c13-c428-405b-b75e-c3777cba7f00.png)

1. React uses pascal case instead of camel case
```js
function TemporaryName() 
```
2. Wrap the function in angle brackets similar to an HTML element
```js
ReactDOM.render(<TemporaryName />, document.getElementByID("root"))
```

![Screenshot 2022-12-15 at 2 21 54 PM](https://user-images.githubusercontent.com/89284873/207959183-c6b0ae3e-8abf-4f34-bf77-ba06a69e439b.png)

## Challenge Part 1

![Screenshot 2022-12-15 at 2 23 06 PM](https://user-images.githubusercontent.com/89284873/207959381-348cf09f-ad9f-41d0-9fd4-3c6974b46afb.png)

```js
import React from "react"
import ReactDOM from "react-dom"

function LearnReact() {
    return (
        <div className="LearnReact">
          <h1>Reasons Why I love React</h1>
           <ol>
              <li>It is fun.</li>
              <li>It is declarative.</li>
              <li>It is compostable.</li>
              <li>It is in demand.</li>
              <li>It is valuable.</li>
           </ol>
        </div>
    )
};

ReactDOM.render(<LearnReact />, document.getElementById("root"))
```

![Screenshot 2022-12-15 at 2 29 53 PM](https://user-images.githubusercontent.com/89284873/207960632-f84db002-f282-4085-94e3-bbad64a704d2.png)

## Challenge Part 2

![Screenshot 2022-12-15 at 2 31 29 PM](https://user-images.githubusercontent.com/89284873/207960931-51256c6e-4e68-40e4-b814-bc24f2de0e8f.png)

```js
import React from "react"
import ReactDOM from "react-dom"

function Page() {
    return (
        <div>
            <header>
                <nav>
                    <img src="./react-logo.png" width="40px" />
                </nav>
            </header>
            <h1>Reasons I'm excited to learn React</h1>
            <ol>
                <li>It's a popular library, so I'll be 
                able to fit in with the cool kids!</li>
                <li>I'm more likely to get a job as a developer
                if I know React</li>
            </ol>
            <footer>
                <small>© 2022 Ash Moreno. All rights reserved.</small>
            </footer>
        </div>
    )
}

ReactDOM.render(<Page />, document.getElementById("root"))
```

![Screenshot 2022-12-15 at 2 37 33 PM](https://user-images.githubusercontent.com/89284873/207962014-9a07531a-bc6b-4f5f-a9bc-10ed77ad0d99.png)

## Custom Components Quiz

Quiz!

1. What is a React component?
- Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML. Components come in two types, Class components and Function components.
- A function that returns React elements. (UI)

2. What's wrong with this code?
```
function myComponent() {
    return (
        <small>I'm tiny text!</small>
    )
}
```

- It needs to be in Pascal Case.

3. What's wrong with this code?
```
function Header() {
    return (
        <header>
            <nav>
                <img src="./react-logo.png" width="40px" />
            </nav>
        </header>
    )
}

ReactDOM.render(Header(), document.getElementById("root"))
```

- The function should be wrapped inside angle brackets like an HTML element, <Header />

