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

## Props

- When React sees an element representing a user-defined component, it passes JSX attributes & children to this component as a single object. The object is known as **props**(properties).
- **props** make a component more reusable(we can call it whatever we want).
- **props** is an object so we can destructure it.
- **props** is immutable, which means a component receiving it, is not allowed to modify it.

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
- We can't pass **props** to a native HTML tag.

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

### Conditional rendering of props

- conditional rendering in React works the same way conditions work in javascript.
- We can either use `if` or _conditional(ternary) operator_ to create elements.

```js
function Card(props) {
  if (props.title) {
    return <h1>{props.title}</h1>;
  }
  return null;
}
```

#### Inline `if` with Logical `&&` Operator

- We can embed logical `&&` operator with JSX by wrapping them in curly braces.

```js
function Navbar(props) {
  return (
    <nav className="navigation">
      <ul className="navigation__menu">
        {props.home && <li>{props.home}</li>}
        {props.projects && <li>{props.projects}</li>}
        {props.contact && <li>{props.contact}</li>}
      </ul>
    </nav>
  );
}
```

#### Inline If-Else with Conditional(ternary) Operator

- We can also use javascript _ternary operator_ to render elements inline.

```js
function HeroSection(props) {
  return (
    <div className="hero-section">
      <button>{props.loggedIn ? "Logged In" : "Logged out"}</button>
    </div>
  );
}
```

### Passing React component as props

- We can pass react components as **props**.

```js
function Footer(props) {
  return {props.children && <footer>{props.children}</footer>};
}

<React.StrictMode>
  <Footer children={<h3>Hello Footer</h3>} />
</React.StrictMode>
```

- **props** can be given a default value.
- Anything can be passed as **props** in React.

## Lists & Keys

- We use JavaScript's `map()` method to create an array of components.
- **Keys** help React identify which items have changed, are added or are removed.
- **Keys** should be given to the elements inside the array to give the elements a stable identity & they must be unique among siblings.

```js
const names = ["Rahul Kumar", "Rohit Kumar", "Ganesh Mahto", "Chulbuli"];

function Card(props) {
  return (
    <div className="card" key={props.id}>
      <h3>{props.name}</h3>
    </div>
  );
}
const cardComponents = names.map(data => {
  return <Card name={data.name} id={data.id} />;
});

<React.StrictMode>
  <main className="cards">{cardComponents}</main>
</React.StrictMode>;
```

## Handling Events

- handling events with React elements are very similar to handling events with DOM elements(JavaScript).
- React events are named using **camelCase** & with JSX, we pass a function as the event handler.

```js
// In HTML
<button onclick="eventHandler()">Click Here</button>
// IN React
<button onClick={eventHandler}>Click Here</button>
```

- In React elements, we can't return `false` to prevent default behavior, we need to control `preventDefault` explicitly.

```js
// In HTML
<form onsubmit="console.log('You clicked submit button');return false">
  <button type="submit">Submit</button>
</form>;

// In React
function Form() {
  function handleSubmit(e) {
    e.preventDefault();
    console.log("You clicked submit button");
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

## State & Lifecycle

- **state** refers to the values that are managed by the component, similar to variables declared inside a function.
- Whenever we have changing values that should be saved/displayed, We use **state**.

> Intially **state** feature could be accessed via class but now we have **state Hook**, which makes a lot simplier to use it.

## Hooks

### Using the state Hook

- Hooks let you use **state** and other React features without writing a class.
