# React

- It is declarative which means it does whatever we say it to do.
- React is **composable**, which means we can create multiple small components(custom/user-defined components) and then can invoke one/more component(s) in another component.
- React component is simply a function which returns React element and it is reusable.
- React element is a javascript object which is obtained when we return jsx code.
- We can use fragement `<></>` to wrap components inside it.
- Components in React can be **stateful** or **stateless**.
  - **stateful** - a component which declares & manages _local state_
  - **stateless** - a component which does not have any _local state_ & side-effects to manage, which means it is a pure function.

```js
import React from "react";
import ReactDOM from "react-dom/client";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <header className="header">
      <h1>Header component</h1>
    </header>
  </React.StrictMode>
);
```

- JSX Code(components) should be nested inside a single parent.

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

- We have to use **PascalCase**(Capitalize first character of each word) instead of **CamelCase** to name a function returning a component.

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
- **props** make a component more reusable(we can name it whatever we want).
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

- Data from **props** is _read-Only_.
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

- We can pass react components also as **props**.

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
const cards = names.map(data => {
  return <Card name={data.name} id={data.id} />;
});

<React.StrictMode>
  <main className="cards--container">{cards}</main>
</React.StrictMode>;
```

## Handling Events

- handling events with React elements are very similar to handling events with DOM elements(JavaScript).
- React events are named using **camelCase** & with JSX, we pass a function as the event handler.

```js
function eventHandler() {
  return 'Hello Ji';
}

// In HTML
<button onclick="eventHandler()">Click Here</button>
// In React
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

- **state** refers to the values which are managed by the component & it is private to the component, similar to variables declared inside a function.
- Whenever we have changing values that should be saved/displayed, We use **state**.
- **state** is mutable.
- Whenever we need the old value of **state** to determine the new value of **state**, we should pass a callback function to our _state setter function_ instead of using **state** directly. This callback will receive the old value of **state** as its parameter which we can then use to determine our new value of **state**.

```js
import { useState } from "react";

export default function Counter() {
  const [counterValue, setCounter] = useState(0);
  const increment = () => setCounter(val => val + 1);

  return (
    <div className="counter">
      <h2>{counterValue}</h2>

      <div className="counter-btns">
        <button className="counter-btn increment-btn" onClick={increment}>
          +
        </button>
      </div>
    </div>
  );
}
```

> Intially **state** feature could be accessed via class but now we have **state Hook**, which makes it a lot simplier to use Hook.

- When, we use object as **state** and want to change state any property then we need to mention other properties also.

```js
function App() {
  const [info, setInfo] = useState({
    name: "Rahul Kumar",
    age: 26,
    isMarried: false
  });

  const toggleState = () => {
    setInfo(prev => {
      return {
        ...prev,
        isMarried: !prev.isMarried
      };
    });
  };

  return (
    <div>
      <h1>{info.name}</h1>
      <h2>{info.age}</h2>

      <span>
        {info.name} {info.isMarried ? "is married" : "is not married"}
      </span>

      <button onClick={toggleState}>Toggle</button>
    </div>
  );
}
```

- We can also pass **state** as **props** in a component.

```js
import { useState }, React from "react";
import ReactDOM  from "react-dom/client";

function Card(props) {
  return (
    <div className="card">
      <h2>{props.title}</h2>
      <p>{props.content}</p>
    </div>
  );
}

function App() {
  const [card, setCard] = useState({
    title: "Sonam is my love",
    content: "Let's find out who is Sonam and what she does"
  });

  const changeCard = () => {
    setCard({
      title: "Sundar is great",
      content: "I am Rahul Kumar Baranwal from India"
    })
  }

  return (<>
    <Card title={card.title} content={card.content}/>
    <button onDoubleClick={changeCard}>change card</button>
  </>)
}


ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

```

- We can also pass a _state setter function_ to Child component.

```js
import { useState } from "react";

const Text = function (props) {
  return (
    <div className="container">
      <h1>
        {props.heading} {props.bool}
      </h1>
      <button onClick={props.toggleText}>Toggle</button>
    </div>
  );
};

const App = () => {
  const [obj, setObj] = useState({
    heading: `Hello value ---> `,
    bool: true
  });

  const toggleText = () => {
    setObj(obj => ({ ...obj, bool: !obj.bool }));
  };

  // Passing state setter function "toggleText"
  return (
    <>
      <Text heading={obj.heading} toggleText={toggleText} />
    </>
  );
};
```

> We should keep state as local(close) as possible with a component.

#### Derived State management

- When we create a new **state** using the **props** coming from another **state**, then it is called **Derived State**.

```js
import { useState } from "react";
import boxesData from "./boxesData";

// Here we are using props coming from another state to create a new state
function Box(props) {
  const [boxOn, setBoxOn] = useState(props.on);
  const toggleBool = () => setBoxOn(val => !val);

  const styles = {
    backgroundColor: boxOn ? "hwb(250 30% 0%/.75)" : "transparent"
  };
  return <div className="box" style={styles} onClick={toggleBool}></div>;
}

const App = () => {
  const [boxes, _] = useState(boxesData);
  const boxComponents = boxes.map(box => <Box key={box.id} on={box.on} />);

  return (
    <>
      <h1>Boxes will be here</h1>
      <main>{boxComponents}</main>
    </>
  );
};
```

#### Unified State management

## Forms

- In React, **textarea** behaves similar to **input** form control (**text, email and number**).

#### Controlled Components

- Those components in which form data is handled by the **component's state**.
- These are predictable since the state of the form elements is handled by the component.
- These enable us to effectively employ form validation to our forms.

```js
function App() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");

  function onSubmit() {
    console.log("Name value: " + name);
    console.log("Email value: " + email);
  }

  return (
    <form onSubmit={onSubmit}>
      <input
        type="text"
        name="name"
        value={name}
        onChange={e => setName(e.target.value)}
        required
      />
      <input
        type="email"
        name="email"
        value={email}
        onChange={e => setEmail(e.target.value)}
        required
      />
      <input type="submit" value="Submit" />
    </form>
  );
}
```

#### Uncontrolled Components

- Those components are those for which the form data is handled by the **DOM** itself.
- The values of the form elements are traditionally controlled by & stored on the **DOM**.
- These components are not predictable since during the lifecycle of a component, the form elements can lose their reference & may be changed/affected by other sources.

```js
function App() {
  const nameRef = useRef();
  const emailRef = useRef();

  function onSubmit() {
    console.log("Name value: " + nameRef.current.value);
    console.log("Email value: " + emailRef.current.value);
  }
  return (
    <form onSubmit={onSubmit}>
      <input type="text" name="name" ref={nameRef} required />
      <input type="email" name="email" ref={emailRef} required />
      <input type="submit" value="Submit" />
    </form>
  );
}
```

## Hooks

- Hooks are special JavaScript functions in React which manage the state's behaviour, side effects and its other features by isolating them from a _functional component_.
- They are used inside a functional component.
- Hooks let you use **state** and other React features without _writing a class_.

### Using the state Hooks

#### useState()

- The **useState** hook takes an initial value and returns an array containing a stateful value and a function to update the value(_state setter function_).
- _State setter function_ updates the value as well as enques a re-rendering of the component.
- _State setter function_ runs **asynchronously**.

```js
import { useState } from "react";

export default function App() {
  const [num, setNum] = useState(0);
  return (
    <>
      <div className="container">
        <p>{num}</p>
        <button onClick={() => setNum(prev => ++prev)}>Increase</button>
      </div>
    </>
  );
}
```

- Each component in React maintains its own state independently.

```js
import {useState} from "react";

const Counter = () => {
  const [num, setNum] = useState(0);
  return (
    <div className="counter-container">
      <p>{num}</p>
      <button onClick={() => setNum(prev => ++prev)}>Increase</button>
    </div>
  );
};

// Each of the Counter component is maintaining its own state independently without affecting others.
export default const App = () => {
  return (
    <>
      <Counter />
      <Counter />
      <Counter />
    </>
  );
};
```

- Along with primitive and non-primitive data types, we can also pass a function inside `useState()`.

```js
import { useState } from "react";

export default function App() {
  const [val, setVal] = useState(() => 5 + 5 + 2);
  return (
    <div className="wrapper">
      <h4>{val}</h4>
    </div>
  );
}
```

#### useReducer()

- It is similar to `useState()`, but with the ability to maintain complex states and lets you _move the state update logic_ from event handlers into a single function outside of your component.
- We can not call it inside **loops or conditions**.
- **Syntax**

```js
const [state, dispatch] = useReducer(reducer, initialArg, init?)
```

##### Paremeters

- `reducer`: It specifies how the state gets updated. It must be pure, should take the state and action as arguments, and should return the next state. **State and action can be of any types**.
- `initialArg`: The value from which the initial state is calculated. It can be **a value of any type**. How the initial state is calculated from it depends on the next `init` argument.
- `init`(optional): The initializer function that specifies how the initial state is calculated. If it’s not specified, the initial state is set to `initialArg`. Otherwise, the initial state is set to the result of calling `init(initialArg)`.

##### Returns

- It returns an array with exactly two values:-

  1. The current state
  2. `dispatch` function takes `action` parameter as an object with a `type` & lets us **update the state to a different value & trigger a re-render**.

- **Examples**

```js
import { useReducer } from "react";

// BASIC EXAMPLE
function reducer(state, action) {
  if (action.type === "incremented_age") {
    return {
      age: state.age + 1
    };
  }
  throw Error("Unknown action.");
}

export default function Counter() {
  const [state, dispatch] = useReducer(reducer, { age: 42 });

  return (
    <>
      <button
        onClick={() => {
          dispatch({ type: "incremented_age" });
        }}
      >
        Increment age
      </button>
      <p>Hello! You are {state.age}.</p>
    </>
  );
}

// COMPLEX EXAMPLE
function reducerFunc(state, action) {
  switch (action.type) {
    case 'incremented_age': {
      /* Nothing will change because React looks for a different object reference and we are having the same object reference*/
      // state.age += 1;
      // return state;
      return {
        ...state,
        age: state.age + 1
      };
    }
    case 'changed_name': {
      return {
        ...state,
        name: action.nextName,
      };
    }
  }
  throw Error('Unknown action: ' + action.type);
}

const initialState = { name: 'Taylor', age: 42 };

export default function Form() {
  const [state, dispatch] = useReducer(reducerFunc, initialState);

  function handleButtonClick() {
    dispatch({ type: 'incremented_age' });
  }

  function handleInputChange(e) {
    dispatch({
      type: 'changed_name',
      nextName: e.target.value
    });
  }

  return (
    <>
      <input
        value={state.name}
        onChange={handleInputChange}
      />
      <button onClick={handleButtonClick}>
        Increment age
      </button>
      <p>Hello, {state.name}. You are {state.age}.</p>
    </>
  );
}
```

#### useMemo()

- It allows us to **memoize expensive functions** so that we can avoid calling them on every render.
- It takes **a function** & **an array of inputs(dependency array)** as parameters.
- **Syntax**

```js
import { useMemo } from "react";

useMemo(function, dependency_array); // useMemo(() => {}, [dependency])
```

- **Examples**

```js
import { useState, useMemo } from "react";

export default function Counter() {
  const [grade, setGrade] = useState(5);
  const countPopulation = grade => {
    return grade ** 2;
  };

  const memoizedVal = useMemo(() => countPopulation(grade), []);

  return (
    <div className="counter">
      <p>Current Grade: {grade}</p>
      <p>Current Population: {memoizedVal}</p>
    </div>
  );
}
```

#### useCallback()

#### useRef()

#### useEffect()

#### useContext()
