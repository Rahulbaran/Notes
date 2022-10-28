# React

- It is declarative which means it does whatever we say to do.
- React is **composable**, which means we can create small components(custom/user-defined components) and then can put them together to create a complete app.
- React component is simply a function which returns React element and it is reusable.
- React element is a javascript object which is obtained when we return jsx code.
- We can use fragement `<></>` to wrap component code inside it.

```js
import React from "react";
import ReactDOM from "react-dom/client";

ReactDOM.createRoot(document.getElementById("root")).render(
  <>
    <header className="header">
      <h1>Header component</h1>
    </header>
  </>
);
```

- JSX Code should be nested inside a single parent.

```js
const HeaderComponent = function () {
  return (
    <>
      <header className="header">
        <h1>Header component</h1>
        <nav className="navigation">
          <ul className="navigation__menu">
            <li>First list</li>
            <li>Second list</li>
            <li>Third list</li>
          </ul>
          >
        </nav>
      </header>
    </>
  );
};

ReactDOM.createRoot(document.querySelector("#root")).render(
  <React.StrictMode>
    <HeaderComponent />
  </React.StrictMode>
);
```

- We have to use **PascalCase**(Capitalize first character on each word) instead of **CamelCase** to name a function returning a particular component.

```js
const FooterComponent = function () {
  return (
    <>
      <footer>
        <p>&copy;Copyright reserved since 2022</p>
      </footer>
    </>
  );
};
```

- When React sees an element representing a user-defined component, it passes JSX attributes & children to this component as a single object. The object is known as **props**(properties).
- **props** make a component more reusable(we can call it whatever we want).

```jsx
const city = "Ranchi";

function Main(properties) {
  return (
    <h1>
      Hello, my name is {properties.name} & I live in {city}
    </h1>
  );
}
ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <>
      <Main name="Rahulbaran" />

      <h1>
        Good morning, <abbr>ISRO</abbr>
      </h1>
    </>
  </React.StrictMode>
);
```

- **props** are Read-Only.
- We can't pass a **props** to native HTML tag.

```jsx
ReactDOM.createRoot(root).render(
  <React.StrictMode>
    <>
      <div blah="hello"></div>
    </>
  </React.StrictMode>
);
```

> All React components must act like pure functions with respect to their props.
