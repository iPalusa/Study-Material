# Lambda Expressions

Lambda expressions in Java provide a concise way to create anonymous functions. They are used for implementing functional interfaces (interfaces with a single abstract method). 

The syntax of a lambda expression in Java consists of the following parts:

1. Parameter List: Enclosed in parentheses and can be empty or contain one or more parameters. If there's only one parameter, you can omit the parentheses. For multiple parameters, use commas.

2. Arrow Token (`->`): Separates the parameter list from the body of the lambda expression.

3. Body: Contains the code to be executed when the lambda expression is invoked. It can be a single expression or a block of statements enclosed in curly braces. 

Here's the general syntax:

```java
(parameters) -> { body }
```

Examples:
1. Lambda expression with no parameters and a single expression:
   ```java
   () -> "Hello, Lambda"
   ```

2. Lambda expression with one parameter and a block of statements:
   ```java
   (int x) -> {
       int result = x * 2;
       System.out.println("Result: " + result);
   }
   ```

3. Lambda expression with multiple parameters and a single expression:
   ```java
   (int a, int b) -> a + b
   ```

4. Lambda expression with a single parameter and a single expression (parentheses can be omitted):
   ```java
   x -> x * x
   ```
   
Lambda expressions are typically used when working with functional interfaces, such as the `Runnable`, `Consumer`, or `Predicate` functional interfaces. The number of parameters and the type of the parameters should match the method signature of the functional interface.

## Functional interfaces

Functional interfaces are a fundamental concept in Java, especially when working with lambda expressions and the functional programming features introduced in Java 8 and later. Here's an explanation of functional interfaces:

**Definition:**
A functional interface is an interface that has exactly one abstract method. It's also known as a Single Abstract Method (SAM) interface. Functional interfaces are used to represent a single unit of behavior, and they can serve as a target type for lambda expressions or method references.

**Characteristics:**

**Single Abstract Method (SAM):** A functional interface has one and only one abstract method. It may have multiple default or static methods, but only one abstract method.

**Annotation (Optional):** Functional interfaces can be annotated with the @FunctionalInterface annotation. This annotation helps to ensure that the interface is indeed a functional interface by causing a compilation error if the interface doesn't adhere to the SAM rule.

**Usage:**
Functional interfaces are commonly used in Java to encapsulate behavior that can be represented by a single function. Some common use cases include:

**Lambda Expressions**: Functional interfaces are used as targets for lambda expressions, allowing concise and expressive code.

**Method References:** They can be used with method references, which are shorthand notations for invoking methods.

1. **Supplier<T>** - `T get()`
   - Provides a value without taking any input.
   ```java
   Supplier<Integer> randomInt = () -> (int)(Math.random() * 100);
   int value = randomInt.get();
   ```

2. **Consumer<T>** - `void accept(T t)`
   - Accepts a value and performs an action without returning a result.
   ```java
   List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
   names.forEach(name -> System.out.println("Hello, " + name));
   ```

3. **Function<T, R>** - `R apply(T t)`
   - Takes an input, processes it, and returns a result.
   ```java
   Function<Integer, String> intToString = num -> "Number: " + num;
   String result = intToString.apply(42);
   ```

4. **Predicate<T>** - `boolean test(T t)`
   - Tests a condition and returns a boolean.
   ```java
   Predicate<Integer> isEven = num -> num % 2 == 0;
   boolean result = isEven.test(5);
   ```

5. **BiFunction<T, U, R>** - `R apply(T t, U u)`
   - Takes two inputs, processes them, and returns a result.
   ```java
   BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
   int sum = add.apply(3, 5);
   ```

Functional interfaces simplify coding by encapsulating behavior within a single method, making it easy to use lambda expressions and method references.

### Creating custom functional interfaces

Creating custom functional interfaces in Java involves defining an interface with a single abstract method (SAM).

**Cheatsheet:**

1. Define the custom functional interface using the `@FunctionalInterface` annotation.
2. The interface should have only one abstract method.
3. Use the custom functional interface to create lambda expressions and method references.

**Explanation:**

1. **Define the Custom Functional Interface:** Use the `@FunctionalInterface` annotation to declare your custom functional interface. For example:

   ```java
   @FunctionalInterface
   public interface MyFunction {
       int apply(int a, int b);
   }
   ```

2. **Single Abstract Method (SAM):** Ensure your custom functional interface has only one abstract method. In this example, the `apply` method is the single abstract method.

3. **Use Lambda Expressions:** You can use your custom functional interface to create lambda expressions and use them in your code. For example:

   ```java
   MyFunction add = (a, b) -> a + b;
   int result = add.apply(5, 3); // Result is 8
   ```

   Here, the `add` lambda expression implements the `apply` method of the `MyFunction` interface.

By following these steps, you can create and use custom functional interfaces in Java to leverage the power of lambda expressions and functional programming.

## Method References

### **Method reference types (e.g., static, instance, constructor references)**

1. **Static Method Reference:**
   - Syntax: `ContainingClass::staticMethodName`
   - Example: `Math::max` refers to the static `max` method in the `Math` class.

2. **Instance Method Reference:**
   - Syntax: `object::instanceMethodName`
   - Example: `System.out::println` refers to the `println` method of the `System.out` object.

3. **Constructor Reference:**
   - Syntax: `ClassName::new`
   - Example: `ArrayList::new` refers to the constructor of the `ArrayList` class.

Method references provide a concise way to refer to methods or constructors, making your code more readable and reducing boilerplate.

### **Using method references with functional interfaces**

**Method Reference Types:**
1. **Static Method Reference:** `Class::staticMethod`
2. **Instance Method Reference:** `instance::instanceMethod`
3. **Instance Method of Particular Object:** `object::instanceMethod`
4. **Constructor Reference:** `Class::new`

Example:
```java
// Static Method Reference
Function<Integer, String> converter = String::valueOf;

// Instance Method Reference
List<String> list = Arrays.asList("apple", "banana", "cherry");
list.forEach(System.out::println);

// Constructor Reference
Supplier<List<String>> listSupplier = ArrayList::new;
```

In these examples, we use different types of method references to simplify functional interface method implementations. Static, instance, and constructor references offer concise ways to refer to methods or constructors without explicitly defining lambda expressions.

## Default Methods

### **Default methods in interfaces**

**Default Methods in Java Interfaces: Cheat Sheet**

- Introduced in Java 8, default methods allow adding new methods to interfaces without breaking implementing classes.
- They provide a default implementation that can be overridden by implementing classes.
- Default methods are marked with the `default` keyword and can be used for backward compatibility.

**Example:**

```java
interface Shape {
    void draw(); // Abstract method

    default void resize() {
        System.out.println("Resizing the shape"); // Default method
    }
}

class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle();
        circle.draw();
        circle.resize(); // Uses the default implementation
    }
}
```

In this example, `resize()` is a default method in the `Shape` interface, and it's available to the `Circle` class without needing to provide an explicit implementation.

Sure, let's provide cheatsheets and explanations for topics 14 and 15:

### **Interface Evolution and Backward Compatibility:**

**Cheatsheet:**
- Interfaces can evolve in Java by adding new methods with default implementations.
- Existing implementations won't break, as they inherit the default method.
- Concrete classes implementing the interface can override the default method.

**Explanation:**
Java allows interfaces to evolve over time while maintaining backward compatibility. New methods with default implementations can be added to interfaces. Existing classes that implement the interface inherit the default implementation. Concrete classes can choose to override the default method if needed.

```java
// Original interface
interface MyInterface {
    void originalMethod();
}

// Later, evolving the interface with a default method
interface MyInterface {
    void originalMethod();

    default void newDefaultMethod() {
        // Default implementation
    }
}

// Existing classes remain compatible and can still be used.
class MyClass implements MyInterface {
    @Override
    public void originalMethod() {
        // Implementation
    }
    // No need to implement newDefaultMethod.
}
```

### **Solving the "Diamond Problem" :**

**Cheatsheet:**
- The "Diamond Problem" occurs in multiple inheritance when a class inherits from two classes with a common method.
- In Java, this is solved by using interfaces, where the class implements both interfaces and explicitly defines the method.

**Explanation:**
The "Diamond Problem" occurs when a class inherits from two classes that both have a common method, causing ambiguity. In Java, this is solved by using interfaces, not classes, to define shared behavior. The class implements both interfaces and explicitly provides an implementation for the common method.

```java
// Define two interfaces with a common method
interface A {
    void commonMethod();
}

interface B {
    void commonMethod();
}

// Class C implements both interfaces and provides an implementation
class C implements A, B {
    @Override
    public void commonMethod() {
        // Resolve ambiguity with a specific implementation
    }
}
```

By implementing both interfaces and providing a concrete implementation, the class `C` resolves the "Diamond Problem" ambiguity.