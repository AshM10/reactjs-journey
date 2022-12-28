# Challenge: Render Props

![Screenshot 2022-12-28 at 11 51 34 AM](https://user-images.githubusercontent.com/89284873/209852631-666b3a4e-5ab0-426a-90a7-e45625503067.png)

![Screenshot 2022-12-28 at 11 51 45 AM](https://user-images.githubusercontent.com/89284873/209852646-03247dbe-6612-48fc-86a5-6ba4fd019d22.png)

![Screenshot 2022-12-28 at 11 51 57 AM](https://user-images.githubusercontent.com/89284873/209852671-080d3756-d197-4e20-8252-762268927033.png)

## [My Solution](https://scrimba.com/scrim/co0e14efbbe209154a901b143)
## [My other solution](https://scrimba.com/scrim/co9a54077af4bf7bebeef63c5)

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

https://user-images.githubusercontent.com/89284873/209854857-0b38540b-4596-468a-9896-9e53029ad916.mov

## Instructor's solution

- remember, in the render props pattern, what we do is acll a function that's being pass to this component i.e. *DataFetcher.js* 
- component doesn't really care about how the component is being used. Instead, it's up to whatever component is using this component i.e. *App.js* .
- what this component cares about is this the maintenance of state and updating it correctly, making the request in this case and returning that data.

*DataFetcher.js*

```js
import React, {Component} from "react"

class DataFetcher extends Component {
    state = {
        loading: false,
        data: null
    }
    
    componentDidMount() {
        this.setState({loading: true})
        fetch(this.props.url)
            .then(res => res.json())
            .then(data => this.setState({data: data, loading: false}))
    }
    
    render() {
        return (
            this.props.children(this.state.data, this.state.loading)
        )
    }
}

export default DataFetcher
```

*App.js*

```js
import React from "react"
import DataFetcher from "./DataFetcher"

function App() {    
    return (
        <div>
            <DataFetcher url="https://swapi.co/api/people/1">
                {(data, loading) => {
                    return (
                        loading ? 
                        <h1>Loading...</h1> :
                        <p>{JSON.stringify(data)}</p>
                    )
                }}
            </DataFetcher>
        </div>
    )
}

export default App
```

## Data Fetching in React

- In React, data fetching refers to the process of retrieving data from a remote server or API (Application Programming Interface) and storing it in a local component state. This data can then be displayed in the React component using JSX (JavaScript XML).

- There are several ways to fetch data in a React application. One common method is to use the fetch API, which is a built-in browser API for making HTTP requests. Here's an example of how you might use fetch to retrieve data from a remote API and store it in a React component:

```js
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    async function fetchData() {
      const response = await fetch('https://example-api.com/endpoint');
      const data = await response.json();
      setData(data);
    }
    fetchData();
  }, []);

  return (
    <div>
      {data ? (
        <div>{data.name}</div>
      ) : (
        <div>Loading...</div>
      )}
    </div>
  );
}
```

- In this example, the useEffect hook is used to perform the data fetching when the component mounts. The fetch function is used to make the HTTP request, and the response.json method is used to parse the response data as JSON. The data is then stored in the component's state using the setData function, which is provided by the useState hook.

- Another popular way to fetch data in a React application is to use a library like Axios, which provides a simple API for making HTTP requests.

```js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function ExampleComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    async function fetchData() {
      const response = await axios.get('https://example-api.com/endpoint');
      setData(response.data);
    }
    fetchData();
  }, []);

  return (
    <div>
      {data ? (
        <div>{data.name}</div>
      ) : (
        <div>Loading...</div>
      )}
    </div>
  );
}
```

- In this example, the axios.get function is used to make the HTTP request, and the response.data property is used to access the data returned by the API. The data is then stored in the component's state using the setData function.

- Overall, data fetching is an important aspect of building applications with React, as it allows you to retrieve and display data from remote sources in your components.

## Why is Data Fetching important?

- Data fetching is important in React because it allows you to retrieve and display data from remote sources in your application. This is useful because it enables you to build dynamic, data-driven applications that can display different content based on the data that is retrieved.

- For example, you might use data fetching to retrieve a list of products from a remote API and display them in a product catalog. You could then use filters or search functionality to allow users to find specific products, or you could display the products in a grid or list view. All of this would be made possible by fetching data from a remote source and storing it in the component state.

- In addition to making it possible to build dynamic, data-driven applications, data fetching is also important because it enables you to decouple the data layer of your application from the presentation layer. This means that you can change the data source or the way that data is retrieved and displayed without having to make changes to the actual components that display the data. This can make it easier to maintain and update your application over time.

- Overall, data fetching is an important aspect of building applications with React because it enables you to build dynamic, data-driven applications that can display different content based on the data that is retrieved, and it allows you to decouple the data layer of your application from the presentation layer.

