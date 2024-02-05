# **Types of Method References:**
## Static method references.
Static method references are a shorthand notation for lambda expressions that call a static method. They allow you to refer to a static method directly using the `::` operator. The syntax for a static method reference is `ClassName::staticMethodName`. Here are examples demonstrating static method references in Java:

### 1. **Example with a Functional Interface:**
```java
import java.util.function.Supplier;

class MyStaticMethods {
    static String myStaticMethod() {
        return "Hello from static method!";
    }
}

public class StaticMethodReferenceExample {
    public static void main(String[] args) {
        // Using a static method reference
        Supplier<String> supplier = MyStaticMethods::myStaticMethod;

        // Getting the result using the get() method
        String result = supplier.get();

        // Printing the result
        System.out.println(result);
    }
}
```

In this example, `MyStaticMethods` has a static method called `myStaticMethod()`. The static method reference `MyStaticMethods::myStaticMethod` is used as a `Supplier<String>` to create a lambda expression that supplies the result of the static method.

### 2. **Example with Stream API:**
```java
import java.util.Arrays;
import java.util.List;

class MyStringUtils {
    static boolean isUpperCase(String str) {
        return str.equals(str.toUpperCase());
    }
}

public class StaticMethodReferenceWithStreamExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("HELLO", "world", "JAVA");

        // Using static method reference with the Stream API
        long count = words.stream()
                .filter(MyStringUtils::isUpperCase)
                .count();

        // Printing the count of uppercase words
        System.out.println("Count of uppercase words: " + count);
    }
}
```

In this example, `MyStringUtils` has a static method called `isUpperCase()`. The static method reference `MyStringUtils::isUpperCase` is used with the `filter` operation in the Stream API to count the number of uppercase words in a list.
## Instance method references.
Instance method references in Java provide a concise way to refer to an instance method of a particular object or to an instance method of an arbitrary object of a particular type. The syntax for an instance method reference is `instance::methodName`. Here are examples demonstrating instance method references:

### 1. **Example with a Functional Interface:**
```java
import java.util.function.Function;

class MyInstanceMethods {
    String myInstanceMethod(String input) {
        return "Hello, " + input;
    }
}

public class InstanceMethodReferenceExample {
    public static void main(String[] args) {
        MyInstanceMethods instanceMethods = new MyInstanceMethods();

        // Using an instance method reference
        Function<String, String> function = instanceMethods::myInstanceMethod;

        // Applying the function to get a result
        String result = function.apply("World");

        // Printing the result
        System.out.println(result);
    }
}
```

In this example, `MyInstanceMethods` has an instance method called `myInstanceMethod(String input)`. The instance method reference `instanceMethods::myInstanceMethod` is used as a `Function<String, String>` to create a lambda expression that applies the instance method to a string input.

### 2. **Example with Stream API:**
```java
import java.util.List;
import java.util.stream.Collectors;

class MyStringUtils {
    boolean isUpperCase(String str) {
        return str.equals(str.toUpperCase());
    }
}

public class InstanceMethodReferenceWithStreamExample {
    public static void main(String[] args) {
        MyStringUtils stringUtils = new MyStringUtils();
        List<String> words = List.of("HELLO", "world", "JAVA");

        // Using instance method reference with the Stream API
        List<String> upperCaseWords = words.stream()
                .filter(stringUtils::isUpperCase)
                .collect(Collectors.toList());

        // Printing the uppercase words
        System.out.println("Uppercase words: " + upperCaseWords);
    }
}
```

In this example, `MyStringUtils` has an instance method called `isUpperCase(String str)`. The instance method reference `stringUtils::isUpperCase` is used with the `filter` operation in the Stream API to filter out uppercase words from a list.

## Constructor references.
Constructor references in Java provide a concise way to refer to a constructor of a class. They allow you to create instances of a class using a shorthand notation. The syntax for a constructor reference is `ClassName::new`. Here are examples demonstrating constructor references:

### 1. **Example with a Functional Interface:**
```java
import java.util.function.Function;

class MyClass {
    private String value;

    // Constructor
    MyClass(String value) {
        this.value = value;
    }

    String getValue() {
        return value;
    }
}

public class ConstructorReferenceExample {
    public static void main(String[] args) {
        // Using a constructor reference
        Function<String, MyClass> constructorRef = MyClass::new;

        // Creating an instance using the apply() method
        MyClass instance = constructorRef.apply("Hello, Constructor Reference!");

        // Printing the value using the instance method
        System.out.println(instance.getValue());
    }
}
```

In this example, `MyClass` has a constructor that takes a `String` parameter. The constructor reference `MyClass::new` is used as a `Function<String, MyClass>` to create a lambda expression that applies the constructor to a string input.

### 2. **Example with Stream API:**
```java
import java.util.List;
import java.util.stream.Collectors;

class Person {
    private String name;

    // Constructor
    Person(String name) {
        this.name = name;
    }

    String getName() {
        return name;
    }
}

public class ConstructorReferenceWithStreamExample {
    public static void main(String[] args) {
        List<String> names = List.of("Alice", "Bob", "Charlie");

        // Using constructor reference with the Stream API
        List<Person> persons = names.stream()
                .map(Person::new)
                .collect(Collectors.toList());

        // Printing the names of the created persons
        persons.forEach(person -> System.out.println(person.getName()));
    }
}
```

In this example, `Person` has a constructor that takes a `String` parameter. The constructor reference `Person::new` is used with the `map` operation in the Stream API to create instances of the `Person` class based on a list of names.

## **Using Method References:**
Arbitrary Instance Method References (ClassName::methodName):

Used for referring to an instance method of an arbitrary object of a particular type.
```java
interface MyInterface {
    void myMethod(String s);
}

class MyClass {
    void myInstanceMethod(String s) {
        System.out.println("Instance method: " + s);
    }
}

public class ArbitraryInstanceMethodReferenceExample {
    public static void main(String[] args) {
        MyInterface myInterface = MyClass::myInstanceMethod;
        myInterface.myMethod("Hello");
    }
}
```