# Wildcards

A wildcard is a symbol used in type declarations to represent an unknown type or a family of related types. Wildcards are often used with generic classes and methods to make them more flexible and adaptable to different data types.

### Unbounded Wildcards(`?`);
An unbounded wildcard represents an unknown type. It is denoted by the question mark `?`. Unbounded wildcards are useful when you want to work with generic types without knowing or specifying the actual type.
```java
import java.util.ArrayList;
import java.util.List;

public class UnboundedWildcardExample {
    public static double sum(List<?> numbers) {
        double total = 0.0;
        for (Object number : numbers) {
            // Since the type is unknown, we can only treat it as Object
            // and perform operations common to all objects (e.g., calling toString).
            System.out.println(number.toString());
        }
        return total;
    }

    public static void main(String[] args) {
        List<Integer> integers = new ArrayList<>();
        integers.add(1);
        integers.add(2);
        integers.add(3);

        List<Double> doubles = new ArrayList<>();
        doubles.add(1.5);
        doubles.add(2.5);
        doubles.add(3.5);

        sum(integers);
        sum(doubles);
    }
}
```
In this example, the sumOfNumbers method takes a list of any type that extends Number. It can work with lists of Integer, Double, or any other class that is a subclass of Number.

### Lower Bounded Wildcard (`? super T`)

A lower bounded wildcard allows a wildcard to represent any type that is a supertype of a specified type. It is denoted by `? super T`, where `T` is the lower bound.
```java
import java.util.List;

public class LowerBoundedWildcardExample {
    public static void addIntegers(List<? super Integer> list) {
        list.add(1);
        list.add(2);
        list.add(3);
    }
}
```
In this example, the addIntegers method takes a list of any type that is a supertype of Integer. It can work with lists of Object, Number, or any other superclass of Integer. This allows adding integers to the list because any element in the list is guaranteed to be able to hold integers.

### Upper Bounded Wildcard (`? extends T`);
An upper bounded wildcard allows a wildcard to represent any type that is a subtype of a specified type. It is denoted by `? extends T`, where `T`is the upper bound.
```java
import java.util.List;

public class UpperBoundedWildcardExample {
    public static double sumOfNumbers(List<? extends Number> numbers) {
        double total = 0.0;
        for (Number number : numbers) {
            total += number.doubleValue();
        }
        return total;
    }
}
```
In this example, the sumOfNumbers method takes a list of any type that extends Number. It can work with lists of Integer, Double, or any other class that is a subclass of Number.

# Bounded Types
Bounded types refer to the use of bounds or restrictions on the types that can be used as type parameters. Bounded types help enforce constraints on the generic type, making the code more flexible and safer. There are two main types of bounded types: upper bounded types and lower bounded types.

### Upper Bounded Type
An upper bounded type in Java generics restricts the generic type to be a subtype of a specified type. It is denoted by the extends keyword.
```java
import java.util.List;

public class UpperBoundedExample {
    // Method that works with a list of numbers or its subtypes
    public static double sumOfList(List<? extends Number> numbers) {
        double sum = 0.0;
        for (Number number : numbers) {
            sum += number.doubleValue();
        }
        return sum;
    }

    public static void main(String[] args) {
        List<Integer> integers = List.of(1, 2, 3, 4, 5);
        List<Double> doubles = List.of(1.1, 2.2, 3.3, 4.4, 5.5);

        System.out.println("Sum of integers: " + sumOfList(integers));
        System.out.println("Sum of doubles: " + sumOfList(doubles));
    }
}
```

### Lower Bounded Type
A lower bounded type in Java generics restricts the generic type to be a supertype of a specified type. It is denoted by the super keyword.
```java
import java.util.ArrayList;
import java.util.List;

public class LowerBoundedExample {
    // Method that adds integers to a list or its supertypes
    public static void addIntegers(List<? super Integer> numbers) {
        for (int i = 1; i <= 5; i++) {
            numbers.add(i);
        }
    }

    public static void main(String[] args) {
        List<Object> objects = new ArrayList<>();
        List<Number> numbers = new ArrayList<>();

        addIntegers(objects);
        addIntegers(numbers);

        System.out.println("Objects: " + objects);
        System.out.println("Numbers: " + numbers);
    }
}
```
### Multiple Bounded Types
Java also supports specifying multiple bounds for a generic type. This means that a type parameter must be a subtype of all the specified types. Use the & symbol to separate multiple bounds.  
```java
public class MultipleBoundedExample<T extends Number & Comparable<T>> {
    private T value;

    public MultipleBoundedExample(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }

    public static void main(String[] args) {
        MultipleBoundedExample<Integer> intExample = new MultipleBoundedExample<>(5);
        MultipleBoundedExample<Double> doubleExample = new MultipleBoundedExample<>(3.14);

        System.out.println("Integer value: " + intExample.getValue());
        System.out.println("Double value: " + doubleExample.getValue());
    }
}
```
In this example, the MultipleBoundedExample class is restricted to accept a type parameter that is both a subtype of Number and implements the Comparable interface. This ensures that the generic type can be compared.