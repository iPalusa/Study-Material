# 1. useImperativeHandle Hook

**Purpose:** `useImperativeHandle` is used to customize the instance value that is exposed when using React `forwardRef`. It allows you to define the instance methods that are accessible externally.

**Syntax:**
```javascript
useImperativeHandle(ref, createHandle, [deps]);
```

- `ref` (RefObject): A ref object created using `useRef`.
- `createHandle` (function): A function that returns an object of properties and methods to be exposed through the ref.
- `deps` (array of dependencies, optional): An array of dependencies, similar to the dependencies array in `useEffect`. If provided, the handle will be updated only when the dependencies change.

**Example:**
```javascript
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const MyComponent = forwardRef((props, ref) => {
  const myRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      myRef.current.focus();
    },
    reset: () => {
      myRef.current.value = '';
    },
  }));

  return <input ref={myRef} />;
});

const App = () => {
  const myRef = useRef();

  return (
    <div>
      <MyComponent ref={myRef} />
      <button onClick={() => myRef.current.focus()}>Focus Input</button>
      <button onClick={() => myRef.current.reset()}>Reset Input</button>
    </div>
  );
}
```

In this example, the `useImperativeHandle` hook allows us to expose the `focus` and `reset` methods of the `input` element to be called externally when using `forwardRef`.

# 2. useLayoutEffect Hook

**Purpose:** `useLayoutEffect` is similar to `useEffect`, but it fires synchronously after all DOM mutations. It's useful when you need to make changes that affect layout immediately, such as measuring the size of a DOM element.

**Syntax:**
```javascript
useLayoutEffect(callback, [deps]);
```

- `callback` (function): A function that contains the code you want to run after layout changes.
- `deps` (array of dependencies, optional): An array of dependencies, similar to the dependencies array in `useEffect`. If provided, the effect will be re-run when the dependencies change.

**Example:**
```javascript
import React, { useState, useLayoutEffect, useRef } from 'react';

const MeasureSize = () => {
  const [size, setSize] = useState({ width: 0, height: 0 });
  const elementRef = useRef();

  useLayoutEffect(() => {
    setSize({
      width: elementRef.current.clientWidth,
      height: elementRef.current.clientHeight,
    });
  }, [elementRef.current.clientWidth, elementRef.current.clientHeight]);

  return (
    <div>
      <div
        ref={elementRef}
        style={{
          width: '200px',
          height: '200px',
          backgroundColor: 'lightblue',
        }}
      >
        Content
      </div>
      <p>Width: {size.width}px</p>
      <p>Height: {size.height}px</p>
    </div>
  );
};
```

In this example, the `useLayoutEffect` hook is used to measure and update the size of a DOM element synchronously after any layout changes.

# 3. useDebugValue Hook

**Purpose:** `useDebugValue` is a custom hook used for adding labels or metadata to custom hooks to help with debugging and development.

**Syntax:**
```javascript
useDebugValue(value, formatFunction);
```

- `value` (any): The value or data to be displayed in the React DevTools.
- `formatFunction` (function, optional): A function that formats the `value` to a string for display in the DevTools. This is optional, and if not provided, React will use the default formatting.

**Example:**
```javascript
import { useDebugValue, useState } from 'react';

function useCustomHook(initialValue) {
  const [value, setValue] = useState(initialValue);

  // Add a debug label to the custom hook
  useDebugValue(value, (value) => `Custom Hook Value: ${value}`);

  return [value, setValue];
}

function App() {
  const [count, setCount] = useCustomHook(0);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <p>Count: {count}</p>
    </div>
  );
}
```

In this example, the `useDebugValue` hook is used to provide a custom label to the `value` exposed by the custom hook for easier debugging in the React DevTools.