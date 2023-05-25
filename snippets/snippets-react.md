## How React Renders

React needs to know where to render the elements it creates. We select the DOM element we want to
render into by using `document.querySelector()`. We then create a React root object. The root object
has a `render()` method that we can use to render React elements into the DOM.

```html
<!--html-->
<div id="root"></div>
```

```jsx
// jsx
const rootElement = document.querySelector("#root");
const root = ReactDOM.createRoot(rootElement);
root.render(<h1>Hello, world</h1>);
```

You'll probably never have to write this code yourself, because it is already included in all
templates and starters. In the real world it usally looks like this:

```jsx
// jsx
const rootElement = document.getElementById("root");
const root = ReactDOM.createRoot();

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

Here we have an imported `<App />` element that is wrapped in `<React.StrictMode>`.

> 💡 `StrictMode` sets up React to run in strict mode. In strict mode React points out potential
> problems in an application.

<details><summary>
💡 React works smart, not hard
</summary>

React only updates the DOM elements that have changed compared to the last render. This is very
efficient and provides a great user experience (focus stays consistent, inputs keep their values,
etc.) as well as a great developer experience (declaritive code is much easier to reason about).

</details>

---

## React Components

React applications are built using components. A component is an independent and reusable piece of the user interface that contains its own structure, logic, and potentially styling.

React components are JavaScript functions that
return React elements. Those elements are then turned into DOM elements by React during the
rendering process.

In order to create a React component, we write a named function (using PascalCase) and have it
return the desired elements using JSX.

```jsx
function MyButton() {
  return (
    <button type="button" className="default-button">
      I'm a button
    </button>
  );
}
```

This is a very powerful concept, because it allows us to reuse the same component in multiple places
in our application.

<details>
> 💡 There are hardly any limitations to how 'small' a component can be (i.e. a button), or how
> 'big' (i.e. an entire page).

> 📙 Read about [**Your First Component**
> in the React Docs](https://react.dev/learn/your-first-component).
>
> **Note**: _Exporting the component_ and _Nesting and organizing components_ are out of scope for this first session.

</details>

---

## `createButton()` with different `valueTypes` as `props`

```jsx
import React from "react";
import "./styles.css";

export default function App() {
  return (
    <Button
      color="lightgreen"
      disabled
      isHappy
      text="Ich bin grün"
      onButton={() => {
        alert("ouch, you hit me!");
      }}
      value={3} // numbers have to be inside {}
    />
  );
}

function Button({ color, disabled, isHappy, text, onButton, value }) {
  return (
    <button
      style={{ backgroundColor: color }}
      disabled={disabled}
      onClick={onButton}
    >
      {text}
      <span role="img" aria-label={isHappy ? "happy" : "sad"}>
        {isHappy ? "🙂" : "😕"}
      </span>
      Value is {value}
    </button>
  );
}
```

<details><summary>Handout // Props</summary>

## React Props

## Learning Objectives

- [ ] Understanding what props are
- [ ] Understanding how to pass props to a component
- [ ] Understanding how to use props in a component
- [ ] Understanding how to render conditionally

---

## Using Props

Props is short for properties. They are a way to pass data to a child component. A component receives a props object as the first function parameter.

Props are [passed to a component as attributes](#passing-props-to-a-component).

```jsx
function UserCard(props) {
  return <div>{props.name}</div>;
}
```

For convenience the props object is often destructured in the function parameter.

```jsx
function UserCard({ name }) {
  return <div>{name}</div>;
}
```

You can choose any names for your props.

> 💡 There are some naming conventions though. Boolean props are often prefixed with `is`, `has` or `should`. For example `isDisabled`, `hasError` or `shouldShow`. Props that take functions are often prefixed with `on`. For example `onClick`, `onSubmit` or `onHover`. Following these conventions makes it easier to understand the purpose of the prop.

Props can be of any type (string, number, array, object, function, ...).

You should treat the props object as immutable and read-only.

---

## Passing Props to a Component

Props are passed to a component as attributes.

```jsx
<UserCard name="Alex" />
```

You can pass any type of data as a prop.

```jsx
<UserCard
  name="Alex"
  age={25}
  onContact={() => console.log("let's chat!")}
  isFavorite={true}
  favoriteFoods={["Pasta", "Salad"]}
  contactDetails={{ email: "alex@neuefische.de", phone: "123456789" }}
/>
```

String props can be passed using double quotes. All other props must be passed using curly braces.

> 💡 Notice the double curly braces for the object. This is because the outer curly braces are used to signify a JavaScript expression. The inner curly braces are used to define an object.

> 💡 There is a shorthand syntax for boolean props. If the value should be `true` you can omit the value.
>
> ```jsx
> <UserCard isFavorite />
> ```

Omitting any attribute will result in the value `undefined` for that prop.

> 📙 Read more about [**Passing props to a Component**
> in the React Docs](https://react.dev/learn/passing-props-to-a-component).

### Conditional Rendering

You can use props to conditionally render parts of a component.

```jsx
function UserCard({ name, isFavorite }) {
  return (
    <div>
      {name}
      {isFavorite ? <span>🌟</span> : null}
    </div>
  );
}
```

> 💡 In JSX `null` is a way to render nothing.

You can not use an `if` statement within JSX because only expressions are allowed. You can use an `if` statement outside of the JSX though.

```jsx
function UserCard({ name, isFavorite }) {
  let favoriteStar = null;
  if (isFavorite) {
    favoriteStar = <span>🌟</span>;
  }

  return (
    <div>
      {name}
      {favoriteStar}
    </div>
  );
}
```

> 📙 Read more about [**Conditional Rendering**
> in the React Docs](https://react.dev/learn/conditional-rendering).

---

## Resources

- [Passing props to a Component in the React Docs](https://react.dev/learn/passing-props-to-a-component)
- [Conditional Rendering in the React Docs](https://react.dev/learn/conditional-rendering)
</details>

---
