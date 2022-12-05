![Screenshot 2022-12-05 at 1 11 45 PM](https://user-images.githubusercontent.com/89284873/205722689-14bc3fc2-e9ea-45be-9ad4-dd47e11a9eed.png)

![Screenshot 2022-12-05 at 1 13 12 PM](https://user-images.githubusercontent.com/89284873/205722961-4edef804-be41-4270-95d2-d1e8302d38cb.png)

![Screenshot 2022-12-05 at 1 13 41 PM](https://user-images.githubusercontent.com/89284873/205723066-a43badfe-a6e2-482b-9855-edc47426d994.png)

![Screenshot 2022-12-05 at 1 13 57 PM](https://user-images.githubusercontent.com/89284873/205723121-da50a407-8e1b-466b-98db-50d1a25bf229.png)

ReactDOM.render() allows you to render something that looks like HTML.

![Screenshot 2022-12-05 at 1 15 04 PM](https://user-images.githubusercontent.com/89284873/205723297-cb6a5c2f-e4cb-4125-b141-9485ee6a1adc.png)

![Screenshot 2022-12-05 at 1 15 22 PM](https://user-images.githubusercontent.com/89284873/205723343-584eb375-13ba-400e-b5fe-090d8b924681.png)

```
ReactDOM.render(<h1>Hello, everyone!</h1>, document.getElementById("root"));

```

![Screenshot 2022-12-05 at 1 31 56 PM](https://user-images.githubusercontent.com/89284873/205726235-5d4bc110-494e-4e15-a050-e3683bf15c3c.png)

![Screenshot 2022-12-05 at 1 32 59 PM](https://user-images.githubusercontent.com/89284873/205726419-9b7342c6-c4ce-4dd7-8710-d4ea0d3210e4.png)

## Why React?

- It's composable
![Screenshot 2022-12-05 at 1 36 10 PM](https://user-images.githubusercontent.com/89284873/205727012-daa60f0e-1082-4afe-9ba8-3a5d4ccf2b6f.png)
![Screenshot 2022-12-05 at 1 42 08 PM](https://user-images.githubusercontent.com/89284873/205728068-03c9b0ab-50db-442a-a565-722b72959c6e.png)
- It's declarative
![Screenshot 2022-12-05 at 1 43 05 PM](https://user-images.githubusercontent.com/89284873/205728195-3f7ab735-6c2c-4a7a-9617-50dd38534f28.png)
![Screenshot 2022-12-05 at 1 52 25 PM](https://user-images.githubusercontent.com/89284873/205730313-33724c72-afa6-4f33-98d5-4f1cf932f20e.png)
```
const h1 = document.createElement("h1")
h1.textContent = "This is an imperative way to program"
h1.className = "header"
document.getElementById("root").append(h1)
```
```
ReactDOM.render(<h1 className="header">Hello, React!</h1>, document.getElementById("root"))
```
- It's a hireable skill
- It's actively maintained by skilled people










