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

# Organize Components

- it is important to have an organizational system that makes sense to you and your group, that is something you've agreed upon in the beginning and stick to as you develop.
- directory should start with a capital letter, the same as the component itself.
![Screenshot 2022-12-19 at 1 38 07 PM](https://user-images.githubusercontent.com/89284873/208506279-2cb5cb91-dc1b-4d49-8fc5-d9209b5b94c9.png)
- import React
- export default the component
- import the component where you want it to be

## Challenge 

![Screenshot 2022-12-19 at 1 44 20 PM](https://user-images.githubusercontent.com/89284873/208507260-538c5415-7d60-45dc-afe3-905e70494a06.png)

![Screenshot 2022-12-19 at 1 46 36 PM](https://user-images.githubusercontent.com/89284873/208507600-666e5250-9cfb-459a-870b-9253dda9c0a1.png)

[Organize Components](https://scrimba.com/scrim/co87b41a4b9ca67e1d3bff420)

![Screenshot 2022-12-19 at 1 50 05 PM](https://user-images.githubusercontent.com/89284873/208508158-c7240091-87d2-48a1-8c4a-80aa5b0ce2a4.png)

