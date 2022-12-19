![Screenshot 2022-12-14 at 1 14 37 PM](https://user-images.githubusercontent.com/89284873/207692101-5cacbb73-81bd-43db-9741-cce7835bd4f3.png)

## Challenge

![Screenshot 2022-12-14 at 1 24 04 PM](https://user-images.githubusercontent.com/89284873/207694261-8554aa50-03fd-44b1-a4ab-ebce3d4c3e3c.png)

## My Solution

```html
<html>
    <head>
        <link rel="stylesheet" href="index.css">
    </head>
    <body>
        <div id="root"></div>
        <script src="index.pack.js"></script>
    </body>
</html>
```

```css
html, body {
    margin: 0;
    padding: 10px;
}

img {
    width: 3rem;
}
```

```js
import React from "react"
import ReactDOM from "react-dom"
import "./index.css"

const hero = (
    <div className="Hero">
      <img src="./react-logo.png" />
      <h1>Fun facts about React</h1>
      <ul>
        <li>Was first released in 2013</li>
        <li>Was originally created by Jordan Walke</li>
        <li>Has well over 100k stars on Github</li>
        <li>Is maintained by Facebook</li>
        <li>Powers thousands of enterprise apps, including mobile apps</li>
      </ul>
    </div>
)

ReactDOM.render(hero, document.getElementById("root"))
```

Note: Custom components 

## Pop Quiz

1. Why do we need to `import React from "react"` in our files?
So react will run and be able to read jsx.
React is what defines jsx, so in order to use jsx we need to import React.

2. If I were to console.log(page) in index.js, what would show up?
![Screenshot 2022-12-14 at 1 33 41 PM](https://user-images.githubusercontent.com/89284873/207697212-4ea4cfe1-a059-4f21-995b-b7e52777068a.png)
A JavaScript Object. React elements that describe what React should eventually add to the real DOM for us.

3. What's wrong with this code:
```
const page = (
    <h1>Hello</h1>
    <p>This is my website!</p>
)
```
Notice that out jsx has two sibling elements. We need our JSX to be nested under a single parent element.
In the future, you can use an empty tag to wrap your jsx. These are called fragments: <> </>

4. What does it mean for something to be "declarative" instead of "imperative"?
just tell what to do, and it will do it for you
i.e: If you ask your friend how to make a peanut butter sandwich, assume that he knows how to do it.
Writing code declaratively is a much developer experience which usually leads with fewer bugs in the end. 

Declarative means I can tell the computer WHAT to do and expect it to handle the details. Imperative means I need to tell it HOW to do each step.

5. What does it mean for something to be "composable"?
We have small pieces that we can put together to make something larger/greater than the individual pieces.



