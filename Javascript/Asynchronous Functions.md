# Callback functions
  
A callback function is a function that is passed as an argument to another function and is executed at a later point in time or in response to an event. Callback functions allow you to write asynchronous or non-blocking code, where the execution of certain tasks is delayed until a specific condition is met or an operation is completed.
```js
// Example 1: Basic Callback Function
function greet(name, callback) {
    console.log("Hello, " + name + "!");
  
    // Invoke the callback function
    callback();
  }
  
  function sayGoodbye() {
    console.log("Goodbye!");
  }
  
  // Pass the sayGoodbye function as a callback to greet
  greet("John", sayGoodbye);
```  
In the above code, the `greet` function takes two arguments: `name` and `callback`. It logs a greeting message to the console and then invokes the callback function. The `sayGoodbye` function is passed as a callback to the `greet` function and is executed after the greeting message is logged.
```js
// Example 2: Asynchronous Callback Function
function fetchData(url, callback) {
    // Simulate an asynchronous operation
    setTimeout(function() {
      const data = "Some data retrieved from " + url;
      callback(data);
    }, 2000);
  }
  
  function processData(data) {
    console.log("Processing data: " + data);
  }
  
  // Pass the processData function as a callback to fetchData
  fetchData("https://example.com/data", processData);
```  
In this code example, we have a function called `fetchData` that simulates an asynchronous operation. It takes two arguments: `url` (representing the URL from which we want to retrieve data) and `callback` (representing the callback function that will be invoked once the data is retrieved).

Inside the `fetchData` function, there is a `setTimeout` function. `setTimeout` is a built-in JavaScript function that allows you to execute a function after a specified delay. In this case, we are using it to simulate the delay that occurs when fetching data from a remote server. The anonymous function passed to `setTimeout` is executed after a 2-second delay.

Within the anonymous function, a `data` variable is created, which contains a string concatenation of "Some data retrieved from " and the provided `url`. This represents the data that would typically be received from the server.

Finally, the `callback` function is invoked with the `data` as its argument. This means that once the asynchronous operation is complete and the data is available, the `callback` function will be called, and the `data` will be passed as an argument to it.

Outside the `fetchData` function, we have another function called `processData`. This function is responsible for processing the retrieved data. In this example, it simply logs a message to the console, displaying the processed data.

To initiate the data retrieval process, we call the `fetchData` function and pass two arguments: the URL (`"https://example.com/data"`) and the `processData` function. This means that once the data is retrieved, the `processData` function will be called with the retrieved data as its argument.

Callback functions are commonly used in JavaScript for handling events, making AJAX requests, working with timers, and performing other asynchronous operations. They allow you to write code that is flexible, modular, and able to handle tasks that may take an unpredictable amount of time to complete.  

# Promises
 
Promises are a JavaScript feature introduced to handle asynchronous operations and simplify asynchronous programming. They provide a way to represent a value that may not be available yet, but will be resolved in the future. Promises allow you to write cleaner and more readable code when dealing with asynchronous tasks.

A Promise can be in one of three states:
1. **Pending**: The initial state of a Promise. It represents that the operation is still in progress and the final value is not available yet.
2. **Fulfilled**: The Promise is fulfilled when the operation completes successfully, and the resulting value is available. Once fulfilled, the Promise transitions to the "resolved" state.
3. **Rejected**: The Promise is rejected when an error or failure occurs during the operation. Once rejected, the Promise transitions to the "resolved" state.

```js
function fetchData(url) {
    return new Promise((resolve, reject) => {
      // Simulate an asynchronous operation
      setTimeout(() => {
        const data = "Some data retrieved from " + url;
        if (data) {
          resolve(data); // Fulfill the Promise with the retrieved data
        } else {
          reject("Error occurred"); // Reject the Promise with an error message
        }
      }, 2000);
    });
  }
  
  function processData(data) {
    console.log("Processing data: " + data);
  }
  
  // Using the Promise
  fetchData("https://example.com/data")
    .then((data) => {
      processData(data);
    })
    .catch((error) => {
      console.log("Error: " + error);
    });
```

In this example, the `fetchData` function returns a Promise. Inside the Promise constructor, an asynchronous operation is simulated using `setTimeout`. If the operation is successful and data is retrieved, the Promise is resolved using the `resolve` function and the retrieved data is passed as an argument. If there is an error or failure, the Promise is rejected using the `reject` function, with an error message as an argument.

To handle the Promise, we use the `.then()` method to define what happens when the Promise is fulfilled, and the `.catch()` method to define what happens when the Promise is rejected. In this case, we call the `processData` function when the Promise is fulfilled, passing the retrieved data as an argument. If the Promise is rejected, we log the error message to the console.

Promises also allow chaining multiple asynchronous operations together using `.then()` and `.catch()`, making it easier to manage complex asynchronous flows and handle errors effectively.

# Async/await

Async/await is a modern JavaScript feature that simplifies asynchronous programming by allowing you to write asynchronous code in a more synchronous and readable manner. It is built on top of JavaScript's Promise object and provides a syntactic sugar for handling promises.

Here's an explanation of how async/await works:

1. **Async Functions**: An async function is a function that is declared using the `async` keyword. It allows you to use the `await` keyword within the function body. The `async` keyword before a function declaration or expression ensures that the function always returns a promise.

2. **Await Expression**: The `await` keyword can only be used inside an async function. It is followed by a Promise object or an expression that evaluates to a Promise. The `await` keyword pauses the execution of the async function until the Promise is resolved or rejected. It allows you to write code that appears synchronous, even though it is asynchronous.

3. **Handling Promises**: When the `await` keyword is used with a Promise, it waits for the Promise to settle (either resolve or reject) before proceeding with the execution of the async function. If the Promise resolves, the result is returned. If the Promise rejects, an exception is thrown, which can be caught using try-catch blocks.
```js
function fetchUserData() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        const userData = { name: "John", age: 25 };
        resolve(userData);
      }, 2000);
    });
  }
  
  async function processData() {
    try {
      const userData = await fetchUserData();
      console.log("User data:", userData);
      // Perform additional operations with userData
    } catch (error) {
      console.error("Error:", error);
    }
  }
  
  processData();
```

In this example, the `fetchUserData` function returns a Promise that resolves after a 2-second delay, simulating the asynchronous retrieval of user data.

The `processData` function is declared as an async function. Inside it, the `await` keyword is used to pause the execution until the `fetchUserData` Promise is resolved. Once resolved, the user data is assigned to the `userData` variable, and it can be further processed or used in subsequent operations.

By using `await`, we avoid chaining `.then()` callbacks or using `.catch()` for error handling. Instead, any errors that occur during the execution of the `await` expression can be caught using a try-catch block.

Using async/await can make asynchronous code more readable and easier to understand, especially when dealing with complex chains of asynchronous operations. It provides a more synchronous-like coding style while still leveraging the power of Promises for handling asynchronous tasks in JavaScript.

# Fetch API

The Fetch API is a modern web API provided by JavaScript that allows you to make network requests, typically to retrieve resources from a server. It provides a more flexible and powerful alternative to traditional methods like XMLHttpRequest (XHR).


### 1. Making a GET request: 
```js
fetch(url)
  .then(response => response.json())
  .then(data => {
    // Process the retrieved data
  })
  .catch(error => {
    // Handle any errors that occur during the request
  });
```

In this example, `fetch()` is used to make a GET request to the specified `url`. It returns a Promise that resolves to the `Response` object representing the server's response. You can chain `.then()` to handle the response and parse it using the `.json()` method, which returns another Promise that resolves to the parsed JSON data. Subsequent `.then()` blocks can be used to process the retrieved data. If any error occurs during the request, it can be caught and handled using the `.catch()` block. 

### 2. Making other types of requests:

```js
fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify(data),
})
  .then(response => {
    // Process the response
  })
  .catch(error => {
    // Handle any errors
  });
```

To make requests other than GET, you can provide additional options as the second parameter to `fetch()`. In this example, a POST request is made by specifying the `method` as 'POST'. Headers can be set using the `headers` option, and the request payload can be included in the `body` option after converting it to JSON using `JSON.stringify()`.

### 3. Handling response status and headers:

```js
fetch(url)
  .then(response => {
    if (response.ok) {
      // Successful response (status in the range 200-299)
      console.log('Request succeeded');
    } else {
      // Handle error response
      console.log('Request failed');
    }
    console.log('Response status:', response.status);
    console.log('Response headers:', response.headers);
  })
  .catch(error => {
    // Handle any errors
  });
```
The `Response` object provides information about the response, including the status code (`response.status`) and headers (`response.headers`). You can use this information to handle different scenarios based on the server's response.

The Fetch API supports various other options and features, such as setting request headers, handling cookies, controlling request modes, and more. It is widely supported in modern browsers and provides a more modern and flexible approach to making network requests in JavaScript. 
# XMLHTTPRequests

XMLHttpRequest (XHR) is an API in web browsers that allows you to send HTTP or HTTPS requests to a server and retrieve data from it. It provides a way to make asynchronous network requests from JavaScript without having to refresh the entire web page.

Here's an example of using XMLHttpRequest to make an HTTP GET request: 

```js
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true); // true for asynchronous

xhr.onreadystatechange = function () {
  if (xhr.readyState === XMLHttpRequest.DONE && xhr.status === 200) {
    const response = JSON.parse(xhr.responseText);
    console.log(response);
  }
};

xhr.send();
```

In the above code, a new instance of the `XMLHttpRequest` object is created using the `new XMLHttpRequest()` constructor.

The `open` method is then called on the `xhr` object to specify the details of the request. It takes three parameters: the HTTP method ("GET" in this case), the URL from which to retrieve data, and a boolean value indicating whether the request should be asynchronous (`true` for asynchronous).

Next, the `onreadystatechange` event handler is set. This function will be called whenever the state of the request changes. Inside the event handler, we check if the `readyState` property of the `xhr` object is `XMLHttpRequest.DONE` (which means the request is complete) and if the `status` property is `200` (indicating a successful response). If both conditions are met, we parse the response using `JSON.parse` and log it to the console.

Finally, the request is sent using the `send` method of the `xhr` object.

Note that this is a basic example for making a GET request, but XMLHttpRequest can also be used for other types of requests, such as POST, PUT, DELETE, etc. Additionally, there are more modern alternatives like the Fetch API and axios, which provide a simpler and more intuitive way to make HTTP requests in JavaScript. 

# Error Handling (Not async)

Throwing and catching errors in JavaScript allows you to handle exceptional situations or unexpected errors that may occur during the execution of your code. You can create and throw custom errors, as well as catch and handle them using try-catch blocks.

### Throwing Errors:
To throw an error in JavaScript, you can use the `throw` statement. It can be used with any value, but it is common to throw an instance of the built-in `Error` object or one of its derived error types. 
```js
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

try {
  const result = divide(10, 0);
  console.log("Result:", result);
} catch (error) {
  console.error("Error:", error.message);
}
```
In the above code, the `divide` function throws an `Error` with a custom error message if the second argument (`b`) is zero. The `throw` statement stops the execution of the function and transfers control to the nearest enclosing `catch` block or terminates the program if there is no catch block.

### Catching Errors:
To catch and handle errors, you can use a `try-catch` block. The `try` block contains the code that may potentially throw an error, and the `catch` block handles the caught error.

In the example above, the `try` block contains the division operation. If an error is thrown within the `try` block, it is caught by the corresponding `catch` block. The caught error is assigned to the `error` variable, and you can access its properties, such as `message`, to get information about the error.

### Error Types and Messages:
JavaScript provides several built-in error types that you can use for specific error scenarios. Some common error types include `Error`, `SyntaxError`, `TypeError`, `ReferenceError`, and `RangeError`. You can also create your own custom error types by extending the `Error` object.

When throwing an error, you can provide a custom error message as a string. The error message helps identify the cause of the error and provides meaningful information for debugging. 
```js
function checkAge(age) {
  if (typeof age !== "number") {
    throw new TypeError("Age must be a number");
  }
  if (age < 18) {
    throw new RangeError("Age must be at least 18");
  }
  // ...
}
```
In the above code, the `checkAge` function throws a `TypeError` if the `age` parameter is not a number and throws a `RangeError` if the age is less than 18. The error messages (`"Age must be a number"` and `"Age must be at least 18"`) provide specific information about the nature of the error. 
# Regular expressions (Not async)
 
Regular expressions (regex) are patterns used to match and manipulate text in strings. They provide a powerful and flexible way to perform pattern matching, validation, and data extraction in JavaScript.

Creating and Using Regular Expressions:
In JavaScript, you can create a regular expression by enclosing the pattern inside forward slashes (/). Here's an example of creating a regular expression that matches a sequence of digits: 
```js
const regex = /\d+/;
```
In this case, `\d` represents a digit character, and `+` indicates that one or more digit characters should be matched. This regex can be used to find sequences of digits in a string.

### Regular Expression Methods:
JavaScript provides several methods to work with regular expressions:

1. `test()`: Tests whether a string matches the regular expression and returns `true` or `false`. 
```js
const regex = /\d+/;
console.log(regex.test("123")); // Output: true
console.log(regex.test("abc")); // Output: false
```
2. `exec()`: Searches the string for a match against the regular expression and returns an array containing the matched result. It can also capture groups within the regular expression. 
```js
const regex = /(\w+)\s(\w+)/;
const match = regex.exec("John Doe");
console.log(match[0]); // Output: John Doe
console.log(match[1]); // Output: John
console.log(match[2]); // Output: Doe
```
3. `match()`: Searches the string for all matches against the regular expression and returns an array of matches. It is commonly used with the global (`g`) flag to find multiple matches. 
```js
const regex = /\d+/g;
const matches = "I have 123 apples and 456 oranges".match(regex);
console.log(matches); // Output: ["123", "456"]
```
4. `replace()`: Replaces matches in a string with a replacement value or function. 
```js
const regex = /apples/g;
const text = "I have many apples, apples are delicious!";
const replacedText = text.replace(regex, "oranges");
console.log(replacedText); // Output: "I have many oranges, oranges are delicious!"
```
5. `split()`: Splits a string into an array of substrings using a separator defined by a regular expression. 
```js
const regex = /\s+/;
const text = "Hello World   JavaScript";
const splittedText = text.split(regex);
console.log(splittedText); // Output: ["Hello", "World", "JavaScript"]
```