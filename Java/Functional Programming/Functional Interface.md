
# **Definition and Characteristics:**
In Java, a functional interface is an interface that contains only a single abstract method (SAM), which is a method without a body. This concept is central to the introduction of functional programming features in Java, particularly with the advent of lambda expressions in Java 8. Here are the key components that define a functional interface:

## 1. **Single Abstract Method (SAM):**
   - A functional interface must have exactly one abstract method. This method represents the behavior of the interface and is the core functionality that can be implemented by lambda expressions or method references.

   - Example of a functional interface:

     ```java
     @FunctionalInterface
     interface MyFunctionalInterface {
         void myAbstractMethod();
     }
     ```

   - It's important to note that a functional interface can still contain other methods (default methods or static methods) as long as there is only one abstract method.

## 2. **`@FunctionalInterface` Annotation:**
   - The `@FunctionalInterface` annotation is an optional but recommended annotation that can be used to explicitly declare an interface as functional. This annotation helps the compiler catch unintended mistakes when attempting to declare more than one abstract method.

   - Example of a functional interface with the `@FunctionalInterface` annotation:

     ```java
     @FunctionalInterface
     interface Calculator {
         int calculate(int a, int b);

         // This would cause a compilation error due to the presence of two abstract methods.
         // int subtract(int a, int b);
     }
     ```

   - While the `@FunctionalInterface` annotation is optional, using it explicitly communicates the intent of the interface to both developers and tools.

### Example Using Lambda Expression:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void myAbstractMethod();
}

public class Main {
    public static void main(String[] args) {
        // Using a lambda expression to implement the abstract method
        MyFunctionalInterface myFunctionalInterface = () -> System.out.println("Executing myAbstractMethod");
        
        // Calling the implemented method
        myFunctionalInterface.myAbstractMethod();
    }
}
```

In this example, `MyFunctionalInterface` is a functional interface with a single abstract method (`myAbstractMethod`). The `@FunctionalInterface` annotation is used to indicate that it is intended to be a functional interface. The lambda expression is then used to provide an implementation for the abstract method.


# **Common Functional Interfaces:**
In Java, the `java.util.function` package provides a set of functional interfaces that cover common use cases for functional programming. Here are explanations and examples for some of the commonly used functional interfaces from this package:

## 1. **`Runnable` Interface:**
   - Represents a task that can be executed concurrently.
   - Has a single `run()` method that takes no arguments and returns no result.

   ```java
   Runnable myRunnable = () -> System.out.println("Executing myRunnable");
   new Thread(myRunnable).start();
   ```

## 2. **`Callable` Interface:**
   - Represents a task that can be executed and returns a result.
   - Similar to `Runnable`, but the `call()` method can throw checked exceptions.

   ```java
   Callable<String> myCallable = () -> "Result from myCallable";
   ```

## 3. **`Comparator` Interface:**
   - Represents a function for comparing two objects.
   - Used for sorting and ordering collections.

   ```java
   List<String> myList = Arrays.asList("Apple", "Orange", "Banana");
   Collections.sort(myList, Comparator.naturalOrder());
   ```

## 4. **`Supplier` Interface:**
   - Represents a supplier of results.
   - Has a `get()` method that takes no arguments and returns a result.

   ```java
   Supplier<String> mySupplier = () -> "Result from mySupplier";
   ```

## 5. **`Consumer` Interface:**
   - Represents an operation that accepts a single input argument and returns no result.
   - Used for actions such as printing, logging, etc.

   ```java
   Consumer<String> myConsumer = s -> System.out.println("Consuming: " + s);
   myConsumer.accept("Hello");
   ```

## 6. **`Function` Interface:**
   - Represents a function that takes one argument and produces a result.
   - Used for transformations and mappings.

   ```java
   Function<Integer, String> myFunction = i -> "Result: " + i;
   ```

## 7. **`Predicate` Interface:**
   - Represents a predicate (boolean-valued function) of one argument.
   - Used for filtering and testing.

   ```java
   Predicate<Integer> isEven = i -> i % 2 == 0;
   ```

# **Built-in Functional Interfaces:**

## `java.util.function` package.
The `java.util.function` package in Java provides a set of functional interfaces that represent different types of functions that can be used with lambda expressions or method references. These interfaces cover a wide range of use cases in functional programming. Here are some of the key functional interfaces in the `java.util.function` package:

### 1. **`Consumer<T>` Interface:**
   - Represents an operation that takes a single argument of type `T` and returns no result.
   - Has a method: `void accept(T t)`.

### 2. **`Supplier<T>` Interface:**
   - Represents a supplier of results.
   - Has a method: `T get()`.

### 3. **`Function<T, R>` Interface:**
   - Represents a function that takes an argument of type `T` and produces a result of type `R`.
   - Has a method: `R apply(T t)`.

### 4. **`Predicate<T>` Interface:**
   - Represents a predicate (boolean-valued function) that takes an argument of type `T`.
   - Has a method: `boolean test(T t)`.

### 5. **`UnaryOperator<T>` Interface:**
   - Represents an operation on a single operand of type `T` and produces a result of type `T`.
   - Extends `Function<T, T>`.

### 6. **`BinaryOperator<T>` Interface:**
   - Represents an operation upon two operands of the same type `T` and produces a result of the same type `T`.
   - Extends `BiFunction<T, T, T>`.

### 7. **`BiFunction<T, U, R>` Interface:**
   - Represents a function that takes two arguments of types `T` and `U` and produces a result of type `R`.
   - Has a method: `R apply(T t, U u)`.

### 8. **`BiPredicate<T, U>` Interface:**
   - Represents a predicate (boolean-valued function) that takes two arguments of types `T` and `U`.
   - Has a method: `boolean test(T t, U u)`.

### 9. **`BiConsumer<T, U>` Interface:**
   - Represents an operation that accepts two input arguments of types `T` and `U` and returns no result.
   - Has a method: `void accept(T t, U u)`.

### 10. **`UnaryOperator<T>` Interface:**
   - Represents an operation on a single operand of type `T` and produces a result of type `T`.
   - Extends `Function<T, T>`.

### 11. **`IntPredicate`, `LongPredicate`, `DoublePredicate` Interfaces:**
   - Specialized versions of `Predicate` for primitive data types.

### 12. **`IntFunction<R>`, `LongFunction<R>`, `DoubleFunction<R>` Interfaces:**
   - Specialized versions of `Function` for primitive input and non-primitive result.

### 13. **`ToIntFunction<T>`, `ToLongFunction<T>`, `ToDoubleFunction<T>` Interfaces:**
   - Represents functions that convert an object of type `T` to primitive types.


### 6. **Optional in Functional Programming:**
   - **Overview of `Optional`:**
     - Avoiding `NullPointerException`.
     - Methods like `map`, `filter`, and `orElse`.

### 7. **Streams in Functional Programming:**
   - **Introduction to Streams:**
     - Basics of streams.
     - Intermediate and terminal operations.

   - **Stream API Methods:**
     - `map`, `filter`, `reduce`, `collect`, etc.
     - Chaining operations.

### 8. **Functional Programming Best Practices:**
   - **Immutability:**
     - Immutable objects and variables.
     - Advantages of immutability.

   - **Side Effects:**
     - Avoiding side effects in functional programming.
     - Pure functions.

   - **Statelessness:**
     - Stateless functions.
     - Functional statelessness.

### 9. **Functional Programming Patterns:**
   - **Functional Composition:**
     - Combining functions.
     - Function composition.

   - **Currying:**
     - Currying functions.
     - Partial application.

### 10. **Concurrency in Functional Programming:**
   - **Parallel Streams:**
     - Overview of parallel streams.
     - Parallelizing operations.

   - **CompletableFutures:**
     - Combining asynchronous computations.
     - Exception handling.

### 11. **Functional Programming Libraries/Frameworks:**
   - **Guava Library:**
     - Functional programming utilities in Guava.

   - **Vavr Library (formerly Javaslang):**
     - Introduction to Vavr.
     - Working with functional types.