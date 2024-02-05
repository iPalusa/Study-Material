# Creating, using, and chaining Optionals
In Java, `Optional` is a container object that may or may not contain a non-null value. It is often used to represent the possibility of a value being absent. Here's a guide on creating, using, and chaining `Optional` in Java:

### 1. Creating Optionals:

#### 1.1. Creating an Optional with a Value:

```java
Optional<String> optionalWithValue = Optional.of("Hello, Optional!");
```

This creates an `Optional` with a non-null value.

#### 1.2. Creating an Empty Optional:

```java
Optional<String> emptyOptional = Optional.empty();
```

This creates an empty `Optional`.

#### 1.3. Creating an Optional with a Nullable Value:

```java
String nullableValue = "Nullable Value";
Optional<String> optionalWithNullable = Optional.ofNullable(nullableValue);
```

This creates an `Optional` that may or may not contain a non-null value.

### 2. Using Optionals:

#### 2.1. Checking if a Value is Present:

```java
Optional<String> optional = Optional.of("Present Value");

if (optional.isPresent()) {
    System.out.println("Value is present: " + optional.get());
} else {
    System.out.println("Value is absent");
}
```

#### 2.2. Conditional Action with `ifPresent`:

```java
Optional<String> optional = Optional.of("Present Value");

optional.ifPresent(value -> System.out.println("Value is present: " + value));
```

This avoids explicit checks and executes the given action if a value is present.

#### 2.3. Default Value with `orElse`:

```java
Optional<String> optional = Optional.empty();
String result = optional.orElse("Default Value");
System.out.println("Result: " + result);
```

This provides a default value if the optional is empty.

#### 2.4. Default Value Supplier with `orElseGet`:

```java
Optional<String> optional = Optional.empty();
String result = optional.orElseGet(() -> "Default Value from Supplier");
System.out.println("Result: " + result);
```

This allows lazy computation of the default value.

#### 2.5. Throwing Exception with `orElseThrow`:

```java
Optional<String> optional = Optional.empty();
String result = optional.orElseThrow(() -> new RuntimeException("Value not present"));
```

Throws an exception if the optional is empty.

### 3. Chaining Optionals:

#### 3.1. `map` Operation:

```java
Optional<String> optional = Optional.of("Present Value");
Optional<Integer> length = optional.map(String::length);
```

Maps the value if present and returns a new `Optional`.

#### 3.2. `flatMap` Operation:

```java
Optional<String> optional = Optional.of("Present Value");
Optional<Character> firstChar = optional.flatMap(s -> Optional.ofNullable(s.charAt(0)));
```

Maps and flattens the result if present.

#### 3.3. Chaining `map` and `flatMap`:

```java
Optional<String> optional = Optional.of("Present Value");
Optional<Integer> result = optional.map(String::length).flatMap(len -> Optional.of(len * 2));
```

You can chain multiple map and flatMap operations.

### 4. Combining Optionals:

#### 4.1. Combining with `filter`:

```java
Optional<String> optional = Optional.of("Present Value");
Optional<String> filtered = optional.filter(s -> s.startsWith("P"));
```

Filters the value based on a condition.

#### 4.2. Combining with `ifPresent`:

```java
Optional<String> optional1 = Optional.of("Hello");
Optional<String> optional2 = Optional.of("Optional");
optional1.ifPresent(value1 -> optional2.ifPresent(value2 -> System.out.println(value1 + " " + value2)));
```

Prints the values if both optionals are present.

### 5. Practical Examples:

#### 5.1. Safe Null Check:

```java
String result = Optional.ofNullable(maybeNull)
                        .orElse("Default Value");
```

#### 5.2. Transformation and Filtering:

```java
String modifiedValue = Optional.ofNullable(maybeNull)
                                .map(String::toUpperCase)
                                .filter(s -> s.length() > 5)
                                .orElse("Default");
```

### Note:
- Always prefer using `map`, `flatMap`, and other functional operations to process values inside Optionals rather than directly accessing the value using `get()` to avoid `NullPointerException`.
- `Optional` is often used in method signatures to indicate that a method may or may not return a value.
- It's not recommended to use `Optional` for fields in classes; it's designed more for return types of methods.


# Handling null values safely
Handling null values safely is crucial to prevent null pointer exceptions and improve the robustness of your code. Here are several approaches in Java to handle null values safely:

### 1. **Null Check:**

```java
if (variable != null) {
    // Perform operations on variable
} else {
    // Handle the case when the variable is null
}
```

This is a basic and commonly used approach to check whether a variable is null before performing any operations on it.

### 2. **Objects.requireNonNull:**

```java
Objects.requireNonNull(variable, "Variable cannot be null");
// Perform operations on variable
```

This method checks if the specified object reference is not null. If it is null, it throws a `NullPointerException` with the specified error message.

### 3. **Ternary Operator:**

```java
String result = (variable != null) ? variable : "Default Value";
// Perform operations on result
```

This is a concise way to handle null values by providing a default value.

### 4. **Optional Class:**

```java
Optional<String> optionalVariable = Optional.ofNullable(variable);
String result = optionalVariable.orElse("Default Value");
// Perform operations on result
```

Using `Optional` is a modern and safer approach for handling potentially null values. It provides functional programming features to work with values that may or may not be present.

### 5. **DefaultIfNull Utility Function:**

```java
public static <T> T defaultIfNull(T value, T defaultValue) {
    return (value != null) ? value : defaultValue;
}

// Usage
String result = defaultIfNull(variable, "Default Value");
// Perform operations on result
```

Creating a utility function can make your code cleaner and more readable, especially if you need to handle null values at multiple places.

### 6. **Objects.requireNonNullElse:**

```java
String result = Objects.requireNonNullElse(variable, "Default Value");
// Perform operations on result
```

This method, introduced in Java 9, returns the first argument if it is non-null; otherwise, it returns the default value provided as the second argument.

### 7. **Using Optional with Map:**

```java
Optional<String> result = Optional.ofNullable(variable).map(String::toUpperCase);
// Perform operations on result
```

`Optional.map` allows you to transform the value inside the `Optional` if it is present.

### 8. **Java 14's `NullPointerException.getMessage`:**

```java
try {
    // Perform operations on variable
} catch (NullPointerException e) {
    String errorMessage = e.getMessage();
    // Handle null case or log the error
}
```

Java 14 introduced the ability to retrieve a detailed message about the null reference that caused the `NullPointerException`. However, relying on this for production code might not be recommended, as it depends on the implementation details of the JVM.


# Methods: `isPresent`, `get`, `orElse`, `orElseGet`, `map`, `flatMap`, `filter`

In Java's `Optional` class, there are several methods that facilitate working with potentially absent values in a safe and expressive manner. Here's an overview of some commonly used methods:

## 1. `isPresent()`:

This method returns `true` if there is a value present in the `Optional`, otherwise, it returns `false`.

```java
Optional<String> optional = Optional.of("Hello");
if (optional.isPresent()) {
    System.out.println("Value is present: " + optional.get());
} else {
    System.out.println("Value is absent");
}
```

## 2. `get()`:

This method returns the value if it is present; otherwise, it throws a `NoSuchElementException`.

```java
Optional<String> optional = Optional.of("Hello");
String value = optional.get();
System.out.println("Value: " + value);
```

## 3. `orElse(T other)`:

This method returns the value if present, otherwise, it returns the specified default value.

```java
Optional<String> optional = Optional.empty();
String result = optional.orElse("Default Value");
System.out.println("Result: " + result);
```

## 4. `orElseGet(Supplier<? extends T> other)`:

This method is similar to `orElse`, but it takes a `Supplier` for the default value, allowing lazy computation.

```java
Optional<String> optional = Optional.empty();
String result = optional.orElseGet(() -> "Default Value from Supplier");
System.out.println("Result: " + result);
```

## 5. `map(Function<? super T, ? extends U> mapper)`:

This method applies the given function to the value if present and returns an `Optional` describing the result.

```java
Optional<String> optional = Optional.of("Hello");
Optional<Integer> length = optional.map(String::length);
```

## 6. `flatMap(Function<? super T, Optional<U>> mapper)`:

This method is similar to `map`, but the provided mapper function returns an `Optional`. It is useful for chaining operations on `Optional` values.

```java
Optional<String> optional = Optional.of("Hello");
Optional<Character> firstChar = optional.flatMap(s -> Optional.ofNullable(s.charAt(0)));
```

## 7. `filter(Predicate<? super T> predicate)`:

This method returns an `Optional` describing the value if present and satisfying the given predicate; otherwise, it returns an empty `Optional`.

```java
Optional<String> optional = Optional.of("Hello");
Optional<String> filtered = optional.filter(s -> s.length() > 3);
```