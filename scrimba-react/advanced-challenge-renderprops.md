# Challenge: Render Props

![Screenshot 2022-12-28 at 11 51 34 AM](https://user-images.githubusercontent.com/89284873/209852631-666b3a4e-5ab0-426a-90a7-e45625503067.png)

![Screenshot 2022-12-28 at 11 51 45 AM](https://user-images.githubusercontent.com/89284873/209852646-03247dbe-6612-48fc-86a5-6ba4fd019d22.png)

![Screenshot 2022-12-28 at 11 51 57 AM](https://user-images.githubusercontent.com/89284873/209852671-080d3756-d197-4e20-8252-762268927033.png)

# [My Solution](https://scrimba.com/scrim/co0e14efbbe209154a901b143)

- In this case, the DataFetcher component is using the render props pattern to pass the loading and data states to the component 
that makes use of it.

- To implement this, you can return the result of calling the render prop function with the loading and data states as arguments. 
For example:

```js
render() {
    const { loading, data } = this.state;
    return this.props.render(loading, data);
}
```

- This will allow the component that uses the DataFetcher to access the loading and data states and use them to render the appropriate UI.

- To make use of the data and loading state in the App component, you can pass a function as the children prop to the DataFetcher 
component. The DataFetcher component should then call this function with the loading and data states as arguments.

- Here's how you can modify the App component to make use of the data and loading state:

```js
import React from "react"
import DataFetcher from "./DataFetcher"

function App() {    
    return (
        <div>
            <DataFetcher url="https://swapi.dev/api/people/1/">
                {(loading, data) => {
                    return loading ? <h1>Loading...</h1> : <p>{JSON.stringify(data)}</p>
                }}
            </DataFetcher>
        </div>
    )
}

export default App
```

- This will render a loading message while the data is being fetched, and display the data once it has been retrieved.

- To make this work, you'll also need to modify the DataFetcher component to call the children function with the loading and data 
states as arguments. Here's how you can do that:

```js
render() {
    const { loading, data } = this.state;
    return this.props.children(loading, data);
}
```

- Then the component will render a loading message while the data is being fetched, and render the data once it has been retrieved.

- If ou just want to use render prop instead of children, do this:

``` js
import React from "react"
import DataFetcher from "./DataFetcher"

function App() {    
    return (
        <div>
            <DataFetcher url="https://swapi.dev/api/people/1/" render={(loading, data) => {
                return loading ? <h1>Loading...</h1> : <p>{JSON.stringify(data)}</p>
            }} />
        </div>
    )
}

export default App
```

