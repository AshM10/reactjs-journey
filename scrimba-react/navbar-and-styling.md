# Navbar & Styling

## Complete the Navbar to match the design

![Screenshot 2023-01-06 at 11 07 58 AM](https://user-images.githubusercontent.com/89284873/211061996-d10ba33c-a58e-4347-a4f9-5a40fe6fc7ea.png)

```js
import React from "react"

export default function Navbar() {
    return (
        <nav>
            <img src="../images/react-icon-small.png" className="nav--icon" />
            <h3 className="nav--logo_text">ReactFacts</h3>
            <h4 className="nav--title">React Course - Project 1</h4>
        </nav>
    )
}
```

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Inter, sans-serif;
}

nav {
    display: flex;
    align-items: center;
    background-color: #21222A;
    height: 90px;
    padding: 30px 25px;
}

.nav--logo_text, .nav--title {
    margin: 0;
}

.nav--logo_text {
    margin-right: auto;
    color: #61DAFB;
    font-weight: 700;
    font-size: 22px;
}

.nav--title {
    color: #DEEBF8;
    font-weight: 600;
}

.nav--icon {
    height: 30px;
    margin-right: 7px;
}
```

