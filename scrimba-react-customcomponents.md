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

