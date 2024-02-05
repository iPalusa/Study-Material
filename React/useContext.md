

# 1. What is Context?
Context is a feature in React that allows you to share data between components without having to pass props through every level of the component tree. It provides a way to manage global state and share data with multiple components.

# 2. When to Use Context?
You should consider using Context when you have data that needs to be accessed by many components at different levels in your component tree.

# 3. The `useContext` Hook API and Usage:

### `useContext(context)`
- The `useContext` Hook is used to access the value of a context object.

```jsx
import React, { useContext } from 'react';

const MyComponent = () => {
  const contextValue = useContext(MyContext); // MyContext is a context object
  return <div>{contextValue}</div>;
};
```

# 4. Creating and Consuming Contexts:

### Creating a Context
- To create a context, use `React.createContext()`.

```jsx
const MyContext = React.createContext();
```

### Providing a Context
- Wrap components that need access to the context in a `Provider`. The `Provider` takes a `value` prop.

```jsx
<MyContext.Provider value="Hello, Context!">
  {/* Your components */}
</MyContext.Provider>
```

### Consuming a Context
- Use the `useContext` Hook to consume the context value.

```jsx
const contextValue = useContext(MyContext);
```

#### Example:

```jsx
// Creating a Context
const MyContext = React.createContext();

// Providing the Context
function App() {
  return (
    <MyContext.Provider value="Hello, Context!">
      <MyComponent />
    </MyContext.Provider>
  );
}

// Consuming the Context
function MyComponent() {
  const contextValue = useContext(MyContext);
  return <div>{contextValue}</div>;
}
```

In the example above, the `MyComponent` can access the value provided by the `MyContext.Provider` without the need for prop drilling.
