# 1. Basics of Side Effects in React
- In React, "side effects" refer to actions that occur outside the regular component rendering cycle, such as data fetching, DOM manipulation, and event listeners.
- Side effects can introduce issues like memory leaks and inconsistent state.
- The `useEffect` hook allows you to manage and control side effects in functional components.

# 2. The `useEffect` Hook API and Usage
- `useEffect` is used to perform side effects in a functional component.
- It takes two arguments: a function and an array of dependencies.
- The function is the side effect you want to perform.
- The array of dependencies (optional) determines when the effect should run.

```jsx
import React, { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // Your side effect code here
  }, [dependency1, dependency2]);
  
  return (
    // JSX for your component
  );
}
```

# 3. Controlling the Execution of Side Effects
- By providing an array of dependencies, you can control when the effect runs. If the array is empty, the effect runs only once after the initial render.
- If dependencies are specified, the effect runs when any of the dependencies change.

```jsx
useEffect(() => {
  // This effect runs after every render
}, []);

useEffect(() => {
  // This effect runs when dependency1 or dependency2 changes
}, [dependency1, dependency2]);
```

# 4. Cleaning Up After Side Effects
- Use the `return` statement in the effect function to define cleanup logic.
- Cleanup runs when the component unmounts or when the dependencies change.
- Common use cases for cleanup include unsubscribing from subscriptions, clearing timers, or removing event listeners.

```jsx
useEffect(() => {
  // Your side effect code here

  return () => {
    // Cleanup logic here
  };
}, [dependency1]);
```

### Example: Fetching Data with `useEffect`
```jsx
import React, { useState, useEffect } from 'react';

function DataFetchingComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    // Fetch data when the component mounts
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return (
    <div>
      {data ? (
        <p>Data: {data}</p>
      ) : (
        <p>Loading data...</p>
      )}
    </div>
  );
}
```
