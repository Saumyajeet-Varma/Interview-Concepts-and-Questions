# Reach Hooks

React Hooks are functions that let you "hook into" React state and lifecycle features from function components. Introduced in React 16.8, hooks enable function components to use features that were previously only available in class components.

## useState

Allows you to add state to functional components.

#### Syntax

```jsx
const [state, setState] = useState(initialState);

```

#### Example

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // state: count

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

## useEffect

Performs side effects in function components (like fetching data, timers, subscriptions).

> In React (and in programming in general), a side effect is any action that affects something outside the scope of the current function or component.

#### Syntax

```jsx
useEffect(() => {
  // side effect
}, [dependencies]);

```
#### Example

```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => setSeconds(s => s + 1), 1000);
    return () => clearInterval(interval); // cleanup
  }, []);

  return <div>Seconds: {seconds}</div>;
}

```

## useContext

Accesses the value of a context in a functional component.

#### Example

```jsx
import React, { useContext, createContext } from 'react';

const UserContext = createContext();

function Greeting() {
  const user = useContext(UserContext);
  return <h1>Hello, {user}!</h1>;
}

function App() {
  return (
    <UserContext.Provider value="Saumyajeet">
      <Greeting />
    </UserContext.Provider>
  );
}

```

## useRef

Returns a mutable ref object that persists for the component's lifetime.

> Common Uses: Access DOM elements, keep mutable values without causing re-renders.

#### Example

```jsx
import React, { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef();

  const focus = () => inputRef.current.focus();

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={focus}>Focus Input</button>
    </>
  );
}

```

## useMemo

Memoizes a computed value to avoid expensive recalculations on every render.

#### Syntax

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

```

#### Example

```jsx
import React, { useMemo, useState } from 'react';

function ExpensiveComponent({ num }) {
  const expensiveValue = useMemo(() => {
    let result = 0;
    for (let i = 0; i < 1e8; i++) result += num;
    return result;
  }, [num]);

  return <div>{expensiveValue}</div>;
}

```

## useCallback

Returns a memoized version of a callback function, useful for optimization.

#### Syntax

```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);

```

#### Example

```jsx
import React, { useState, useCallback } from 'react';

function Button({ handleClick }) {
  return <button onClick={handleClick}>Click</button>;
}

function Parent() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => setCount(c => c + 1), []);

  return (
    <>
      <p>{count}</p>
      <Button handleClick={increment} />
    </>
  );
}

```

## useReducer

An alternative to `useState` for more complex state logic using a reducer function.

#### Syntax

```jsx
const [state, dispatch] = useReducer(reducer, initialState);

```

#### Example

```jsx
import React, { useReducer } from 'react';

const reducer = (state, action) => {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    case 'decrement': return { count: state.count - 1 };
    default: return state;
  }
};

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}

```

## useLayoutEffect

Similar to `useEffect`, but fires synchronously after all DOM mutations.

> Use Case: Measure layout, update DOM before browser paint.

#### Example

```jsx
import React, { useLayoutEffect, useRef } from 'react';

function LayoutExample() {
  const divRef = useRef();

  useLayoutEffect(() => {
    divRef.current.style.color = 'red';
  }, []);

  return <div ref={divRef}>This will be red instantly</div>;
}

```

## useImperativeHandle

Customizes the instance value exposed by `ref` when using `forwardRef`.

> Use Case: Expose specific methods from child to parent.

#### Example

```jsx
import React, { useImperativeHandle, useRef, forwardRef } from 'react';

const CustomInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => inputRef.current.focus(),
  }));

  return <input ref={inputRef} />;
});

function Parent() {
  const ref = useRef();

  return (
    <>
      <CustomInput ref={ref} />
      <button onClick={() => ref.current.focus()}>Focus Input</button>
    </>
  );
}

```

## useId

Generate unique IDs for accessibility and hydration in SSR.

#### Example

```jsx
import React, { useId } from 'react';

function Form() {
  const id = useId();
  return (
    <>
      <label htmlFor={id}>Name</label>
      <input id={id} type="text" />
    </>
  );
}

```

## useTransition

Improves user experience by prioritizing urgent updates over transitions.

```jsx
import React, { useState, useTransition } from 'react';

function List({ items }) {
  const [isPending, startTransition] = useTransition();
  const [input, setInput] = useState('');

  const handleChange = e => {
    const val = e.target.value;
    setInput(val);
    startTransition(() => {
      // simulate filtering large list
    });
  };

  return (
    <>
      <input value={input} onChange={handleChange} />
      {isPending && <p>Loading...</p>}
    </>
  );
}

```

## useDeferredValue

Defers re-rendering of non-urgent updates for better UI responsiveness.

#### Example

```jsx
import React, { useState, useDeferredValue } from 'react';

function SearchResults({ query }) {
  const deferredQuery = useDeferredValue(query);

  return <p>Showing results for: {deferredQuery}</p>;
}

```

## useSyncExternalStore

Used for subscribing to external stores, supports concurrent rendering.

> Use Case: Redux, Zustand, etc.

#### Example

```jsx
import { useSyncExternalStore } from 'react';

function subscribe(callback) {
  window.addEventListener('resize', callback);
  return () => window.removeEventListener('resize', callback);
}

function getSnapshot() {
  return window.innerWidth;
}

function WindowWidth() {
  const width = useSyncExternalStore(subscribe, getSnapshot);
  return <div>Window width: {width}</div>;
}

```

## useInsertionEffect

Allows CSS-in-JS libraries to inject styles before layout and paint.

> Rarely used directly by app developers.

# Summary Table

| Hook                   | Purpose                           |
| ---------------------- | --------------------------------- |
| `useState`             | State management                  |
| `useEffect`            | Side effects                      |
| `useContext`           | Context consumption               |
| `useRef`               | Mutable references, DOM access    |
| `useMemo`              | Memoize computed values           |
| `useCallback`          | Memoize callback functions        |
| `useReducer`           | Complex state logic               |
| `useLayoutEffect`      | DOM mutations before paint        |
| `useImperativeHandle`  | Ref custom API for parent         |
| `useId`                | Unique ID generation              |
| `useTransition`        | Non-blocking UI updates           |
| `useDeferredValue`     | Postpone update rendering         |
| `useSyncExternalStore` | External store sync (Redux, etc.) |
| `useInsertionEffect`   | Inject styles before paint        |
