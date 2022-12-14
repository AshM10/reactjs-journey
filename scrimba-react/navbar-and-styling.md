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

# Main.js

## Build the main section

Skip 2 aspects of the design for now:
1. The colored bullets in the list
2. The larger React logo on the side

![Screenshot 2023-01-06 at 11 32 52 AM](https://user-images.githubusercontent.com/89284873/211066053-5852aa8d-ea8b-4f3c-9d55-2da5be42a45a.png)

[My Solution](https://scrimba.com/scrim/coae644ab8051094701580a95)

```Main.js
import React from "react"

export default function Main() {
    return (
        <main>
            <h1 className="main--title">Fun facts about React</h1>
            <ul className="main--facts">
                <li>Was first released in 2013</li>
                <li>Was originally created by Jordan Walke</li>
                <li>Has well over 100K stars on GitHub</li>
                <li>Is maintained by Facebook</li>
                <li>Powers thousands of enterprise apps, including mobile apps</li>
            </ul>
        </main>
    )
}
```

```css
main {
    padding: 57px 27px;
    color: white;
}

.main--title {
    margin: 0;
    font-size: 39px;
    letter-spacing: -0.05em;
}

.main--facts {
    margin-top: 46px;
    max-width: 400px;
}

.main--facts > li {
    line-height: 19px;
    padding-block: 10px;
}
```

## Challenge

- Color the bullets

![Screenshot 2023-01-06 at 11 43 03 AM](https://user-images.githubusercontent.com/89284873/211068444-e0cf9449-a5dc-4eab-aca1-8d6052b0f6ae.png)

[The Marker pseudo element](https://developer.mozilla.org/en-US/docs/Web/CSS/::marker) - not accepted by all browsers

```css
.main--facts > li::marker {
    font-size: 1.4rem;
    color: #61DAFB;
}
```

- Add background Logo

Challenge: Place the gray react logo in the background

Don't use an `img` element, but rather set it as the
`background-image` of the `main` element.

Hint: you'll need to use the following properties:
- background-image
- background-repeat
- background-position

(Or the shorthand `background` property with values for all
those other properties)

[My Solution](https://scrimba.com/scrim/co0e74109808c76267c07368a) - I had a hard time changing the color of the background image.

```css
main {
    padding: 57px 27px;
    color: white;
    background-image: url(./images/react-icon-large.png);
    background-repeat: no-repeat;
    background-position: right 75%;
}
```

![Screenshot 2023-01-06 at 12 01 18 PM](https://user-images.githubusercontent.com/89284873/211071376-66191b4a-c79e-4bf4-a8a5-72ab7191f368.png)

