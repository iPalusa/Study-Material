# Definition and Purpose
Streams in Java represent a sequence of elements and provide a powerful and expressive way to process collections of data. The Stream API was introduced in Java 8 to streamline and enhance the manipulation of collections using functional programming concepts. Streams allow developers to express complex data processing operations concisely, providing a more declarative and expressive style of coding.

### Key Concepts:

1. **Definition of Streams:**
   - A stream is a sequence of elements that can be processed in parallel or sequentially.
   - Streams don't store data; they operate on the source data structures (e.g., collections, arrays) and produce a result.
   - Streams support a functional programming paradigm, allowing developers to use operations like `map`, `filter`, `reduce`, etc.

2. **Purpose of Streams and Stream API:**
   - **Conciseness and Readability:**
     - Streams allow for more concise and readable code by expressing complex operations as a series of chained methods.
   - **Declarative Style:**
     - Developers can focus on "what to achieve" rather than "how to achieve" the result, making code more declarative.
   - **Parallel Processing:**
     - Streams can leverage parallel processing to perform operations on multiple elements concurrently, improving performance for large datasets.
   - **Lazy Evaluation:**
     - Many stream operations are lazy, meaning they don't process elements until they are needed. This can lead to more efficient processing.

# Stream creation: Collections, Arrays, `Stream.of()`
In Java, streams can be created from various sources, including collections, arrays, and using the `Stream.of()` method. Here are examples for creating streams from these sources:

### 1. **Creating Streams from Collections:**
```java
import java.util.List;
import java.util.stream.Stream;

public class StreamFromCollectionsExample {
    public static void main(String[] args) {
        // Creating a List
        List<String> myList = List.of("Apple", "Banana", "Orange", "Grapes");

        // Creating a stream from a List
        Stream<String> streamFromList = myList.stream();

        // Performing operations on the stream
        streamFromList
            .filter(fruit -> fruit.length() > 5)
            .forEach(System.out::println);
    }
}
```

### 2. **Creating Streams from Arrays:**
```java
import java.util.Arrays;
import java.util.stream.Stream;

public class StreamFromArraysExample {
    public static void main(String[] args) {
        // Creating an array
        String[] myArray = {"Java", "Python", "C++", "JavaScript"};

        // Creating a stream from an array
        Stream<String> streamFromArray = Arrays.stream(myArray);

        // Performing operations on the stream
        streamFromArray
            .filter(language -> language.length() > 3)
            .forEach(System.out::println);
    }
}
```

### 3. **Creating Streams using `Stream.of()`:**
```java
import java.util.stream.Stream;

public class StreamOfExample {
    public static void main(String[] args) {
        // Creating a stream using Stream.of()
        Stream<String> streamOfString = Stream.of("One", "Two", "Three", "Four", "Five");

        // Performing operations on the stream
        streamOfString
            .filter(word -> word.length() > 3)
            .forEach(System.out::println);
    }
}
```

These examples demonstrate how to create streams from collections (`List`), arrays, and using the `Stream.of()` method. Once the stream is created, various stream operations, such as `filter`, `map`, and `forEach`, can be performed on the elements. Streams provide a powerful and expressive way to process data in Java.

# Intermediate operations: `map`, `filter`, `flatMap`, `sort`, `distinct`, `peek`
Intermediate operations in the Stream API in Java are operations that transform or filter the elements of a stream. These operations do not produce a final result or trigger the actual processing of the stream until a terminal operation is applied. Here are some common intermediate operations:

## 1. **`map` Operation:**
The `map` operation in the Stream API is used to transform each element of the stream using a provided function. It returns a new stream consisting of the results of applying the given function to the elements of the original stream. Here's an example demonstrating the `map` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class MapOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the map operation to transform each string to uppercase
        List<String> uppercasedWords = words.stream()
                                           .map(String::toUpperCase)
                                           .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("Uppercased words: " + uppercasedWords);
    }
}
```

In this example:

- The `words` list contains strings: "Java", "Stream", "API".
- The `map` operation is applied to the stream of strings. The provided function `String::toUpperCase` is used to transform each string to uppercase.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Original words: [Java, Stream, API]
Uppercased words: [JAVA, STREAM, API]
```

## 2. **`filter` Operation:**
The `filter` operation in the Stream API is used to select elements from a stream based on a specified condition. It returns a new stream that contains only the elements that satisfy the given predicate. Here's an example demonstrating the `filter` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class FilterOperationExample {
    public static void main(String[] args) {
        // Original list of numbers
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Using the filter operation to select even numbers
        List<Integer> evenNumbers = numbers.stream()
                                          .filter(number -> number % 2 == 0)
                                          .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original numbers: " + numbers);
        System.out.println("Even numbers: " + evenNumbers);
    }
}
```

In this example:

- The `numbers` list contains integers from 1 to 10.
- The `filter` operation is applied to the stream of numbers. The provided predicate `number -> number % 2 == 0` is used to select only the even numbers.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Original numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Even numbers: [2, 4, 6, 8, 10]
```

## 3. **`flatMap` Operation:**
The `flatMap` operation in the Stream API is used to flatten nested collections or maps into a single stream. It transforms each element of the stream into zero or more elements and then flattens the results into a single stream. This is particularly useful when dealing with nested structures. Here's an example demonstrating the `flatMap` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class FlatMapOperationExample {
    public static void main(String[] args) {
        // List of lists containing words
        List<List<String>> listOfLists = Arrays.asList(
                Arrays.asList("Java", "Python"),
                Arrays.asList("Stream", "Lambda"),
                Arrays.asList("API", "Functional")
        );

        // Using the flatMap operation to flatten the nested lists
        List<String> flatList = listOfLists.stream()
                                          .flatMap(List::stream)
                                          .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original list of lists: " + listOfLists);
        System.out.println("Flattened list: " + flatList);
    }
}
```

In this example:

- `listOfLists` is a list of lists, where each inner list contains words.
- The `flatMap` operation is applied to the stream of lists. The `List::stream` function is used to transform each inner list into a stream of its elements.
- The result is a single stream containing all the elements from the nested lists.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Original list of lists: [[Java, Python], [Stream, Lambda], [API, Functional]]
Flattened list: [Java, Python, Stream, Lambda, API, Functional]
```

## 4. **`sort` Operation:**
The `sort` operation in the Stream API is used to sort the elements of a stream. It returns a new stream with the elements sorted according to their natural order or a specified comparator. Here's an example demonstrating the `sort` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class SortOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API", "Sort", "Example");

        // Using the sort operation to sort the strings alphabetically
        List<String> sortedWords = words.stream()
                                        .sorted()
                                        .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("Sorted words: " + sortedWords);
    }
}
```

In this example:

- The `words` list contains strings: "Java", "Stream", "API", "Sort", "Example".
- The `sort` operation is applied to the stream of strings. The elements are sorted alphabetically based on their natural order.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Original words: [Java, Stream, API, Sort, Example]
Sorted words: [API, Example, Java, Sort, Stream]
```

You can also use the `sorted` operation with a custom comparator to specify a different sorting order. For example, sorting by string length:

```java
List<String> sortedByLength = words.stream()
                                   .sorted((str1, str2) -> Integer.compare(str1.length(), str2.length()))
                                   .collect(Collectors.toList());

System.out.println("Sorted by length: " + sortedByLength);
```

Output:
```
Sorted by length: [API, Java, Sort, Stream, Example]
```

## 5. **`distinct` Operation:**
The `distinct` operation in the Stream API is used to eliminate duplicate elements from a stream. It returns a new stream containing unique elements, preserving the order of the original elements. Here's an example demonstrating the `distinct` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class DistinctOperationExample {
    public static void main(String[] args) {
        // Original list of strings with duplicates
        List<String> wordsWithDuplicates = Arrays.asList("Java", "Stream", "API", "Java", "Example");

        // Using the distinct operation to remove duplicates
        List<String> distinctWords = wordsWithDuplicates.stream()
                                                       .distinct()
                                                       .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original words with duplicates: " + wordsWithDuplicates);
        System.out.println("Distinct words: " + distinctWords);
    }
}
```

In this example:

- The `wordsWithDuplicates` list contains strings with duplicates: "Java", "Stream", "API", "Java", "Example".
- The `distinct` operation is applied to the stream of strings, resulting in a new stream with unique elements.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Original words with duplicates: [Java, Stream, API, Java, Example]
Distinct words: [Java, Stream, API, Example]
```

The `distinct` operation is useful when you want to ensure that the elements in the stream are unique. It's important to note that the uniqueness is determined based on the `equals` method of the elements. If the elements are complex objects, make sure the class overrides the `equals` method appropriately.


## 6. **`peek` Operation:**
The `peek` operation in the Stream API is used for debugging and analysis purposes. It allows you to perform an action on each element of the stream without modifying the elements. The `peek` operation is an intermediate operation, and it returns a new stream that is identical to the original stream. It can be useful for logging, debugging, or simply observing the elements as they pass through the stream pipeline. Here's an example demonstrating the `peek` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class PeekOperationExample {
    public static void main(String[] args) {
        // Original list of numbers
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        // Using the peek operation to print each element before mapping
        List<Integer> squaredNumbers = numbers.stream()
                                             .peek(num -> System.out.println("Processing: " + num))
                                             .map(n -> n * n)
                                             .collect(Collectors.toList());

        // Printing the result
        System.out.println("Squared numbers: " + squaredNumbers);
    }
}
```

In this example:

- The `numbers` list contains integers from 1 to 5.
- The `peek` operation is applied to the stream of numbers. It logs each element before the `map` operation.
- The `map` operation is applied to square each number.
- The result is collected into a new list using the `collect` method with `Collectors.toList()`.

Output:
```
Processing: 1
Processing: 2
Processing: 3
Processing: 4
Processing: 5
Squared numbers: [1, 4, 9, 16, 25]
```

The `peek` operation allows you to inspect the elements as they flow through the stream without altering them. It's a useful tool for understanding the behavior of your stream operations, especially in complex stream pipelines. However, be cautious not to use `peek` for side effects that modify the state of the elements, as it may lead to unexpected behavior.


# Terminal operations: `forEach`, `collect`, `reduce`, `find`, `count`, `min`, `max`
Terminal operations in the Stream API in Java are operations that produce a final result or a side-effect. When a terminal operation is applied to a stream, it triggers the actual processing of the stream. Here are some common terminal operations:

### 1. **`forEach` Operation:**
The `forEach` operation in the Stream API is a terminal operation that performs an action for each element of the stream. It allows you to execute a specified action on each element without transforming or collecting the elements into a new data structure. The `forEach` operation is typically used for side effects, such as printing or updating external state. Here's an example demonstrating the `forEach` operation:

```java
import java.util.Arrays;
import java.util.List;

public class ForEachOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the forEach operation to print each element
        words.stream().forEach(word -> System.out.println("Element: " + word));
    }
}
```

In this example:

- The `words` list contains strings: "Java", "Stream", "API".
- The `forEach` operation is applied to the stream of strings. It prints each element using the provided lambda expression.
- The `forEach` operation is a terminal operation, meaning it triggers the actual processing of the stream.

Output:
```
Element: Java
Element: Stream
Element: API
```

### 2. **`collect` Operation:**
The `collect` operation in the Stream API is a terminal operation that transforms the elements of a stream into a different form, usually a collection like a `List`, `Set`, or `Map`. It allows you to specify how the elements should be accumulated and combined into a result container. The `collect` operation is flexible and can be customized using various `Collector` implementations provided in the `Collectors` utility class. Here's an example demonstrating the `collect` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class CollectOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the collect operation to transform elements into a List
        List<String> collectedList = words.stream()
                                         .map(String::toUpperCase)
                                         .collect(Collectors.toList());

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("Collected list: " + collectedList);
    }
}
```

In this example:

- The `words` list contains strings: "Java", "Stream", "API".
- The `collect` operation is applied to the stream of strings. The `Collectors.toList()` collector is used to transform the elements into a `List`.
- The `collect` operation is a terminal operation, meaning it triggers the actual processing of the stream.

Output:
```
Original words: [Java, Stream, API]
Collected list: [JAVA, STREAM, API]
```

You can customize the `collect` operation by using other collectors such as `Collectors.toSet()`, `Collectors.toMap()`, or even creating your own custom collectors. The `collect` operation is powerful and versatile, allowing you to accumulate stream elements into various types of result containers.

### 3. **`reduce` Operation:**
The `reduce` operation in the Stream API is a terminal operation that performs a reduction on the elements of the stream to produce a single result. It takes two parameters: an identity value and an associative accumulation function. The identity value serves as the initial value for the reduction, and the accumulation function combines two elements at a time. The result is the reduced value. Here's an example demonstrating the `reduce` operation:

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class ReduceOperationExample {
    public static void main(String[] args) {
        // Original list of numbers
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        // Using the reduce operation to calculate the sum
        Optional<Integer> sum = numbers.stream()
                                       .reduce((a, b) -> a + b);

        // Printing the result
        System.out.println("Original numbers: " + numbers);
        System.out.println("Sum: " + sum.orElse(0)); // Using orElse to handle the case when the result is absent
    }
}
```

In this example:

- The `numbers` list contains integers from 1 to 5.
- The `reduce` operation is applied to the stream of numbers. The provided lambda expression `(a, b) -> a + b` represents the accumulation function for summing two elements at a time.
- The result is an `Optional` that contains the sum of all elements.

Output:
```
Original numbers: [1, 2, 3, 4, 5]
Sum: 15
```

The `reduce` operation can be used for various types of reductions, such as finding the maximum or minimum value, concatenating strings, or any other associative operation. It's important to note that the `reduce` operation returns an `Optional` because the stream might be empty, resulting in no reduction. You can use methods like `orElse` or `orElseThrow` to handle the case when the result is absent.


### 4. **`find` Operations (`findFirst`, `findAny`):**
The `findFirst` and `findAny` operations in the Stream API are terminal operations that return an `Optional` containing an element from the stream that matches a given predicate. Both operations are suitable for scenarios where you want to retrieve an arbitrary element from the stream that satisfies a condition. However, there are some differences between them:

#### 1. `findFirst` Operation:

- The `findFirst` operation returns the first element of the stream that matches the given predicate.
- If the stream is sequential, the order of elements is deterministic, and `findFirst` returns the first element encountered during the traversal of the stream.
- In parallel streams, the operation may return any element from the stream, but it is still consistent and does not depend on the specific characteristics of the elements.

Example:

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class FindFirstOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the findFirst operation to get the first element
        Optional<String> firstElement = words.stream().findFirst();

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("First element: " + firstElement.orElse("No element found"));
    }
}
```

Output:
```
Original words: [Java, Stream, API]
First element: Java
```

#### 2. `findAny` Operation:

- The `findAny` operation returns any element from the stream that matches the given predicate.
- In sequential streams, it behaves similarly to `findFirst` and returns the first element encountered.
- In parallel streams, it can return any element from the stream, making it suitable for parallel processing.

Example:

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class FindAnyOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the findAny operation to get any element
        Optional<String> anyElement = words.stream().findAny();

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("Any element: " + anyElement.orElse("No element found"));
    }
}
```

Output:
```
Original words: [Java, Stream, API]
Any element: Java
```

### 5. **`count` Operation:**
The `count` operation in the Stream API is a terminal operation that returns the count of elements in the stream. It does not take any parameters and simply provides the number of elements present in the stream. Here's an example demonstrating the `count` operation:

```java
import java.util.Arrays;
import java.util.List;

public class CountOperationExample {
    public static void main(String[] args) {
        // Original list of strings
        List<String> words = Arrays.asList("Java", "Stream", "API");

        // Using the count operation to get the number of elements
        long count = words.stream().count();

        // Printing the result
        System.out.println("Original words: " + words);
        System.out.println("Number of elements: " + count);
    }
}
```

Output:
```
Original words: [Java, Stream, API]
Number of elements: 3
```

In this example:

- The `words` list contains strings: "Java", "Stream", "API".
- The `count` operation is applied to the stream of strings, providing the total number of elements in the stream.
- The result is a `long` value representing the count of elements.

The `count` operation is often used when you need to determine the size of the stream, especially in scenarios where you want to know how many elements match a certain condition. It is a simple and efficient way to obtain the size of the stream without collecting the elements into a new data structure.

### 6. **`min` and `max` Operations:**
The `min` and `max` operations in the Stream API are terminal operations that return the minimum and maximum element of a stream, respectively. These operations take a comparator as an argument to determine the order of elements. If no comparator is provided, the natural order of the elements is used. Here's an example demonstrating both `min` and `max` operations:

```java
import java.util.Arrays;
import java.util.List;
import java.util.Optional;

public class MinMaxOperationExample {
    public static void main(String[] args) {
        // Original list of integers
        List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);

        // Using the min operation to find the minimum element
        Optional<Integer> minNumber = numbers.stream().min(Integer::compareTo);

        // Using the max operation to find the maximum element
        Optional<Integer> maxNumber = numbers.stream().max(Integer::compareTo);

        // Printing the results
        System.out.println("Original numbers: " + numbers);
        System.out.println("Minimum number: " + minNumber.orElse(null));
        System.out.println("Maximum number: " + maxNumber.orElse(null));
    }
}
```

Output:
```
Original numbers: [3, 1, 4, 1, 5, 9, 2, 6]
Minimum number: 1
Maximum number: 9
```

In this example:

- The `numbers` list contains integers.
- The `min` operation is applied to the stream of numbers, using `Integer::compareTo` as the comparator.
- The `max` operation is applied in a similar manner.
- Both operations return `Optional` values to handle the case when the stream is empty.

You can provide your own comparator to `min` and `max` based on your specific requirements. The `min` and `max` operations are useful when you need to find the smallest or largest element in a stream, respectively.