# Styling with Classes

![Screenshot 2022-12-19 at 1 12 21 PM](https://user-images.githubusercontent.com/89284873/208501839-1dd03102-2180-4b08-adce-bd5ac9857646.png)

## Challenge 1

![Screenshot 2022-12-19 at 1 12 59 PM](https://user-images.githubusercontent.com/89284873/208501924-72b4abc3-597b-4908-a558-b52f3e338800.png)

```js
function Header() {
    return (
        <header>
            <nav className="nav">
                <img src="./react-logo.png" width="40px" />
                <ul className="nav-items">
                    <li>Pricing</li>
                    <li>About</li>
                    <li>Contact</li>
                </ul>
            </nav>
        </header>
    )
}
```

## Challenge 2

![Screenshot 2022-12-19 at 1 15 58 PM](https://user-images.githubusercontent.com/89284873/208502435-5fc45905-4699-4c89-af0f-553bd3dc3f62.png)


```css
.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-items {
    list-style: none;
    display: flex;
}

.nav-items > li {
    padding: 10px;
}
```

## Challenge 3

![Screenshot 2022-12-19 at 1 20 06 PM](https://user-images.githubusercontent.com/89284873/208503119-cb01d71a-9089-4d55-a32f-64167be38eaf.png)

```js
function Header() {
    return (
        <header>
            <nav className="nav">
                <img src="./react-logo.png" className="nav-logo" />
                <ul className="nav-items">
                    <li>Pricing</li>
                    <li>About</li>
                    <li>Contact</li>
                </ul>
            </nav>
        </header>
    )
}
```

```css
.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-logo {
    width: 60px;
}

.nav-items {
    list-style: none;
    display: flex;
}

.nav-items > li {
    padding: 10px;
}
```

## Challenge 4

![Screenshot 2022-12-19 at 1 23 02 PM](https://user-images.githubusercontent.com/89284873/208503610-529d066d-e6fa-499a-acd2-dde5574a3217.png)

```js
import React from "react"
import ReactDOM from "react-dom"

function Header() {
    return (
        <header>
            <nav className="nav">
                <img src="./react-logo.png" className="nav-logo" />
                <ul className="nav-items">
                    <li>Pricing</li>
                    <li>About</li>
                    <li>Contact</li>
                </ul>
            </nav>
        </header>
    )
}

function Footer() {
    return (
        <footer className="footer">
            <small>© 2022 Ash Moreno. All rights reserved.</small>
        </footer>
    )
}

function MainContent() {
    return (
        <div className="main">
            <h1>Reasons I'm excited to learn React</h1>
            <ol>
                <li>It's a popular library, so I'll be 
                able to fit in with the cool kids!</li>
                <li>I'm more likely to get a job as a developer
                if I know React</li>
            </ol>
        </div>
    )
}

function Page() {
    return (
        <div className="App">
            <Header />
            <MainContent />
            <Footer />
        </div>
    )
}

ReactDOM.render(<Page />, document.getElementById("root"))
```

```css
.App {
    padding: 1rem 2rem;
}

.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #a56c6c;
    color: whitesmoke;
}

.nav-logo {
    width: 60px;
}

.nav-items {
    list-style: none;
    display: flex;
}

.nav-items > li {
    padding: 10px;
}

.main {
    background-color: #f3b6b6;
    padding: 2rem 1rem;
    color: #915858;
}

.footer {
    background-color: #915858;
    padding: 1rem;
    color: whitesmoke;
}
```

![Screenshot 2022-12-19 at 1 33 07 PM](https://user-images.githubusercontent.com/89284873/208505373-fcba7e32-6e80-4a91-8660-49cee3b06552.png)

