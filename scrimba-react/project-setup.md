# React Site Project Setup

## Challenge

```
/**
Challenge: Project setup

- Create a `components` folder
- Create the following components in separate files inside
  the components folder.  In each one, just render an `h1` 
  with the name of the component (e.g. return <h1>Navbar goes here</h1>):
    - Navbar
    - Main
- Create an App component outside the components folder (sibling to
  the index.js file)
    - Have App render the Navbar and Main components
- Import and render the App component inside of index.js using ReactDOM
    - At this point you should have your "Navbar goes here" etc. showing up
      in the mini-browser.
- Go to Google fonts and get the "Inter" font with weights 400, 600, and 700.
  Put the links to those fonts ABOVE the style.css link in index.html (Use
  the `<link/>` elements instead of the @import or npm options for getting
  the fonts. You may need to do some extra research to figure out how this 
  works if you haven't done it before)
*/
```

[My Solution to the Challenge](https://scrimba.com/scrim/co11d466f87fc5bb1b3ea5356)

![Screenshot 2022-12-19 at 2 45 25 PM](https://user-images.githubusercontent.com/89284873/208518147-73972c8d-5cc9-47df-9230-96abcabfa3a4.png)

```index.html
<html>
    <head>
        <!-- Google Font: Inter -->
        <link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin><link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
        
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div id="root"></div>
        <script src="index.pack.js"></script>
    </body>
</html>
```

```style.css
:root {
    --primary-font-family: font-family: 'Inter', sans-serif;
}
```

```index.js
import React from "react"
import ReactDOM from "react-dom"
import App from "./App.js"

function Index() {
  return (
    <div>
      <App />
    </div>
  )
}

ReactDOM.render(<Index />, document.getElementById("root"))
```

```App.js
import React from "react"
import Navbar from "./components/Navbar.js"
import Main from "./components/Main.js"


export default function App() {
    return (
        <div className="container">
            <Navbar />
            <Main />
        </div>
    )
}
```

```Main.js
import React from "react"

export default function Main() {
    return (
        <h1>Main goes here</h1>
    )
}
```

```Navbar.js
import React from "react"

export default function Navbar() {
    return (
        <h1>Navbar goes here</h1>
    )
}
```

- [Access the Figma File here](https://www.figma.com/file/xA1rJVQOorqMW6xjGdBLcI/ReactFacts?node-id=0%3A1&t=M1DW61i0BVXnP0Jq-0)

- [Duplicated Figma File](https://www.figma.com/file/xdlLu27W7KO7pxLlOtn7E5/ReactFacts-(Copy)?node-id=0%3A1&t=Ed15kJzSrwu8t3Gf-0)

# Quick FIgma Walkthrough

- Sign up with Google
- Choose free tier
- Skip team name
- Explore by yourself
- [Intro to Figma for Developers](https://www.youtube.com/watch?v=ybc2gkvjMDs)

