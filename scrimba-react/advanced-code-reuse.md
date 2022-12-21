# Code Reuse in React

- a really important aspect in being a React developer is understanding the methods and design patterns that have emerged as React has matured
- similar goal: avoid Repetition

## DRY

- Don't Repeat Yourself
- more room for human error, more room for bugs

- Inheritance is what drives OOP, includes classes, subsclasses, inheriting traits from superclasses and so forth
- Composition is a way to compose your code structure by pulling together the bits and pieces you need

## Which one should we use when creating our React applications?

-You should always prefer COMPOSITION over INHERITANCE in React: [Composition Over Inheritance](https://www.youtube.com/watch?v=wfMtDGfHWpA)

![Screenshot 2022-12-21 at 3 11 18 PM](https://user-images.githubusercontent.com/89284873/209003419-a1a67ec5-e28f-4272-9e20-395a8f7abe58.png)

- [React Documentation](https://reactjs.org/docs/composition-vs-inheritance.html#so-what-about-inheritance)

1. Components with props - you can use your component all over your app anytime you need it, pass props and render them differently depending on which props you pass to them
2. Children
3. Higher-order Components
4. Render props

*When React introduced HOOKS, both Higher-order Components and Render props became outdated.*

