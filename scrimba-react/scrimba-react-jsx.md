![Screenshot 2022-12-05 at 1 56 55 PM](https://user-images.githubusercontent.com/89284873/205731138-793fd980-2d5f-4d6e-943c-90c4d5164a5f.png)

## JSX

- Stands for JavaScriptXML
- Think of it as a sort of a flavor of JavaScript that looks a lot like HTML
![Screenshot 2022-12-05 at 1 58 22 PM](https://user-images.githubusercontent.com/89284873/205731419-ec9709c5-fd23-4af6-8956-f257b44f0f0c.png)
![Screenshot 2022-12-05 at 1 59 15 PM](https://user-images.githubusercontent.com/89284873/205731583-d64ccf3a-36b1-4405-8413-4e1dbf0b5fda.png)
![Screenshot 2022-12-05 at 1 59 21 PM](https://user-images.githubusercontent.com/89284873/205731593-f51ca3ec-a860-4a39-9f95-638e85651b53.png)
![Screenshot 2022-12-05 at 1 59 41 PM](https://user-images.githubusercontent.com/89284873/205731649-de22c7e5-83ea-4c20-859e-e693cbde2858.png)
![Screenshot 2022-12-05 at 2 00 00 PM](https://user-images.githubusercontent.com/89284873/205731693-69a31b8f-b154-4b6c-aaa8-e3aef05f574c.png)
![Screenshot 2022-12-05 at 2 00 21 PM](https://user-images.githubusercontent.com/89284873/205731751-6495ccc9-46de-4657-ba28-773f1e2c97fa.png)
- JSX is kind of like a function that when it's run, returns an object that React can interpret and use to create actual element that it can put on the screen for us.
- Remember to always return a single parent element.
![Screenshot 2022-12-05 at 2 03 13 PM](https://user-images.githubusercontent.com/89284873/205732236-08b2ccf4-e8ed-4fde-ab2d-540142ed8da1.png)
![Screenshot 2022-12-05 at 2 04 42 PM](https://user-images.githubusercontent.com/89284873/205732525-5152fd69-0fb7-48b2-92c7-f9b4d6ead0e8.png)

## Challenge

![Screenshot 2022-12-05 at 2 06 13 PM](https://user-images.githubusercontent.com/89284873/205732789-644b7a39-f8da-43d1-adfc-fc24db3baf0d.png)
![Screenshot 2022-12-05 at 2 09 25 PM](https://user-images.githubusercontent.com/89284873/205733257-6a2eb662-c7c9-4818-a4f8-3d14d9fdb89e.png)
![Screenshot 2022-12-05 at 2 11 40 PM](https://user-images.githubusercontent.com/89284873/205733718-4a6fc1bc-e858-4b3f-8b78-29a473abd3af.png)

## Drag and Drop Deploy with Netlify
- using babel
- sign in netlify
- click setup and continue
- scrimba, click the gear, download as zip
- go to netlify drop site
- drag and drop your entire folder into the site
- make sure you drop the whole folder

![Screenshot 2022-12-12 at 1 40 29 PM](https://user-images.githubusercontent.com/89284873/207138591-7c099813-fc18-4f9a-8cbe-dc3c186134cb.png)

![Screenshot 2022-12-12 at 1 43 14 PM](https://user-images.githubusercontent.com/89284873/207139166-caaba5ae-da8d-4e02-8376-4f1edbe55cd9.png)

## Goodbye, CDNs

- add the dependencies that you need:
![Screenshot 2022-12-12 at 1 45 18 PM](https://user-images.githubusercontent.com/89284873/207139579-ff6f271a-dd80-4c08-8827-fb8d672782fa.png)

```
import React from "react"
```
![Screenshot 2022-12-12 at 1 46 50 PM](https://user-images.githubusercontent.com/89284873/207139865-31c5823e-25b4-4bcf-92c0-0cacc0bf5c29.png)
this is where the jsx syntax is defined.
note: react 17 and above no longer require you to import react for it to work

```
import ReactDOM from "react-dom"
```
![Screenshot 2022-12-12 at 1 49 15 PM](https://user-images.githubusercontent.com/89284873/207140309-16eabc69-d5e7-403e-84a5-8a7b1fb909f7.png)

## Update: New React18 createRoot API

- the change has to do with how React renders its root element
![Screenshot 2022-12-12 at 1 51 34 PM](https://user-images.githubusercontent.com/89284873/207140770-8e32b519-c047-4064-b4b9-c89a21a510ff.png)
![Screenshot 2022-12-12 at 1 51 53 PM](https://user-images.githubusercontent.com/89284873/207140842-5155b1cf-09a2-4e48-8a20-dcfb51f24296.png)
![Screenshot 2022-12-12 at 1 52 05 PM](https://user-images.githubusercontent.com/89284873/207140876-3455da5d-cb32-4e2d-8178-9edd1197699d.png)

- first change
```
import ReactDOM from "react-dom/client"
```

- second: create a root first and then use that root to render what you want
![Screenshot 2022-12-12 at 1 54 13 PM](https://user-images.githubusercontent.com/89284873/207141315-86cb97a1-01ca-4dfa-9b2b-aa583eede80d.png)
```
ReactDOM.createRoot(document.getElementByID("root")).render(navbar)
```

- how the documentation renders the root
![Screenshot 2022-12-12 at 1 56 16 PM](https://user-images.githubusercontent.com/89284873/207141713-a5fe425f-5925-45eb-a81e-ca77ae452b3c.png)

## Thought experiment: use.append() instead of ReactDOM.render()?

Challenge:
![Screenshot 2022-12-12 at 1 57 51 PM](https://user-images.githubusercontent.com/89284873/207142004-a0efbfd0-723b-4394-8bc1-6f6f0990bb20.png)
![Screenshot 2022-12-12 at 2 05 20 PM](https://user-images.githubusercontent.com/89284873/207143848-efb21df4-bf94-4fbc-a564-b91ac53b55a0.png)
![Screenshot 2022-12-12 at 2 05 33 PM](https://user-images.githubusercontent.com/89284873/207143880-39201b6e-677f-45ee-b4c9-40096d937ca7.png)
![Screenshot 2022-12-12 at 2 05 45 PM](https://user-images.githubusercontent.com/89284873/207143910-c5f0c0fa-c023-49a3-8f35-0bbda9a1a4fd.png)
```
document.getElementByID("root").append(JSON.stringify(page))
```
- this is to remind you that jsx returns plain JavaScript
- it has nothing to do with the DOM
- it's only when we try to render it with ReactDOM.render() that react can take these JavaScript objects and turn them into real DOM elements that the browser can interpret

![Screenshot 2022-12-12 at 2 08 11 PM](https://user-images.githubusercontent.com/89284873/207144324-ae3b661e-ca8b-49ff-8b07-f70a448b4dac.png)

![Screenshot 2022-12-12 at 2 10 08 PM](https://user-images.githubusercontent.com/89284873/207144650-814f4a15-5f0a-4fbc-8829-2e453b973eef.png)


