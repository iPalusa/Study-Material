# 1. **Introduction to Comparators:**
## Overview of the `Comparator` Interface:

The `Comparator` interface in Java is part of the `java.util` package and provides a means of defining custom ordering for objects. It is particularly useful when the natural ordering of objects is not suitable, or when working with classes that do not implement the `Comparable` interface. The primary method in the `Comparator` interface is the `compare(T o1, T o2)` method, which takes two objects of type `T` and returns an integer value indicating their order. By implementing this method, you can define the logic for comparing objects according to specific criteria.

## Purpose of Using Comparators in Java:

1. **Custom Sorting Logic:**
   - Comparators allow developers to define custom sorting orders for objects based on criteria that may not be intrinsic to the objects themselves.

2. **Flexibility in Sorting:**
   - Using comparators provides flexibility in sorting objects in different ways without modifying the objects' class or relying on their natural ordering.

3. **Working with External Classes:**
   - When you need to sort objects of classes that you didn't write and cannot modify, comparators offer a way to impose a specific order.

4. **Multiple Sorting Criteria:**
   - Comparators allow you to specify multiple criteria for sorting, making it possible to achieve compound sorting based on various attributes.

5. **Dynamic Sorting:**
   - Comparators provide a way to dynamically change the sorting order at runtime, offering adaptability in different scenarios.

6. **Null Handling:**
   - Comparators allow developers to handle null values gracefully during sorting operations.

## Comparison with the `Comparable` Interface:

1. **Comparable Interface:**
   - The `Comparable` interface is part of the Java language and is typically implemented by classes whose instances can be ordered.
   - Objects that implement `Comparable` provide a natural ordering, and the comparison logic is part of the object's class.
   - The natural order is established by the `compareTo` method, which is invoked by sorting methods such as `Collections.sort` or `Arrays.sort`.

2. **Comparator Interface:**
   - The `Comparator` interface is separate from the objects being compared and allows external definition of the comparison logic.
   - It is often used when:
      - The class doesn't implement `Comparable`.
      - A different sorting order is needed than the natural order.
      - Dynamic or multiple sorting criteria are required.

3. **Multiple Comparators:**
   - While `Comparable` allows a class to define a single natural order, multiple comparators can be created for the same class using the `Comparator` interface.

4. **Flexibility:**
   - Comparators provide greater flexibility in choosing and changing the sorting criteria at runtime, making them suitable for more dynamic scenarios.



# 2. **Comparator Interface Methods:**
## `compare(T o1, T o2)`: Understanding the Method Used for Object Comparison

The `compare` method is a fundamental part of the `Comparator` interface in Java. It is responsible for comparing two objects of type `T` and determining their order. Here's an overview of the method signature and its behavior:

### Method Signature:

```java
int compare(T o1, T o2);
```

- **Parameters:**
  - `o1`: The first object to be compared.
  - `o2`: The second object to be compared.

- **Return Value:**
  - An integer value indicating the relationship between the two objects:
    - Negative value: `o1` is less than `o2`.
    - Zero: `o1` is equal to `o2`.
    - Positive value: `o1` is greater than `o2`.

### Method Behavior:

1. **Consistent with Equals:**
   - The `compare` method should be consistent with the `equals` method. If `compare(o1, o2)` returns zero, then `o1.equals(o2)` should return `true`.

2. **Handling Null Values:**
   - The method should be able to handle null values for `o1` and `o2`. The exact behavior (e.g., treating null as less than non-null) depends on the specific sorting logic.

3. **Symmetry:**
   - The comparison should be symmetric, meaning `compare(o1, o2)` should have the same result as `compare(o2, o1)`.

4. **Transitivity:**
   - If `compare(o1, o2)` is negative and `compare(o2, o3)` is negative, then `compare(o1, o3)` should also be negative.

## Implementing the `compare` Method to Define Custom Sorting Logic

When implementing the `compare` method, you are defining the rules for ordering objects. Here's a step-by-step guide to implementing custom sorting logic:

1. **Identify Sorting Criteria:**
   - Determine the criteria based on which objects should be ordered. This could be a single criterion or a combination of multiple criteria.

2. **Use Object Properties:**
   - Access the relevant properties of `o1` and `o2` to make comparisons. This might involve invoking methods or accessing fields, depending on the structure of your objects.

3. **Perform Comparison:**
   - Compare the relevant properties to establish the order. Use standard comparisons (`<`, `==`, `>`) or helper methods, as needed.

4. **Handle Null Values:**
   - If your sorting logic involves handling null values, ensure that your implementation can correctly compare objects with null values.

5. **Return Result:**
   - Based on the comparison, return a negative value if `o1` is less than `o2`, zero if they are equal, or a positive value if `o1` is greater than `o2`.

### Example Implementation:

```java
import java.util.Comparator;

public class CustomComparator implements Comparator<MyObject> {

    @Override
    public int compare(MyObject o1, MyObject o2) {
        // Example: Sorting by a property 'name' in ascending order
        if (o1.getName() == null && o2.getName() == null) {
            return 0; // Both names are null, consider them equal
        } else if (o1.getName() == null) {
            return -1; // o1 has a null name, so it comes before o2
        } else if (o2.getName() == null) {
            return 1; // o2 has a null name, so it comes before o1
        } else {
            return o1.getName().compareTo(o2.getName());
        }
    }
}
```

In this example, the `compare` method sorts `MyObject` instances based on their "name" property in ascending order. The null values are handled, ensuring a consistent and meaningful ordering.

# 3. **Sorting Collections with Comparators:**
## Sorting Lists using `Collections.sort(List<T> list, Comparator<? super T> c)`.
```java
import java.util.Collections;
import java.util.Comparator;
import java.util.List;
import java.util.ArrayList;

public class SortingExample {
    public static void main(String[] args) {
        // Create a Person class
        class Person {
            private String name;
            private int age;

            public Person(String name, int age) {
                this.name = name;
                this.age = age;
            }

            public String getName() {
                return name;
            }

            public int getAge() {
                return age;
            }

            @Override
            public String toString() {
                return "Person{" +
                        "name='" + name + '\'' +
                        ", age=" + age +
                        '}';
            }
        }

        // Create a list of Person objects
        List<Person> personList = new ArrayList<>();
        personList.add(new Person("Alice", 25));
        personList.add(new Person("Bob", 20));
        personList.add(new Person("Charlie", 30));

        // Display the unsorted list
        System.out.println("Unsorted List:");
        for (Person person : personList) {
            System.out.println(person);
        }

        // Create a Comparator to sort persons by age in ascending order
        Comparator<Person> ageComparator = Comparator.comparingInt(Person::getAge);

        // Sort the list using Collections.sort and the custom comparator
        Collections.sort(personList, ageComparator);

        // Display the sorted list
        System.out.println("\nSorted List (by age):");
        for (Person person : personList) {
            System.out.println(person);
        }
    }
}
```
### Sorting Arrays using `Arrays.sort(T[] a, Comparator<? super T> c)`.
```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;

    // Constructors, getters, setters...

    // Example: Custom Comparator for sorting Persons by age in descending order
    public static class AgeComparator implements Comparator<Person> {
        @Override
        public int compare(Person person1, Person person2) {
            return Integer.compare(person2.getAge(), person1.getAge());
        }
    }

    // Constructors, getters, setters...
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    // Other methods, if any...
}

public class SortingArraysExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30),
                new Person("Bob", 25),
                new Person("Charlie", 35)
        };

        // Print the array before sorting
        System.out.println("Before Sorting:");
        for (Person person : people) {
            System.out.println(person.getName() + " - " + person.getAge() + " years old");
        }

        // Sort the array using Arrays.sort and a custom comparator
        Arrays.sort(people, new Person.AgeComparator());

        // Print the array after sorting
        System.out.println("\nAfter Sorting (by age in descending order):");
        for (Person person : people) {
            System.out.println(person.getName() + " - " + person.getAge() + " years old");
        }
    }
}
```
# 4. **Lambda Expressions and Comparators:**
Using lambda expressions in Java provides a concise way to write comparators, especially when the comparison logic is relatively simple. In the context of comparators, lambda expressions can replace the traditional anonymous class syntax. Let's explore the syntax of lambda expressions for comparators with examples:

## Traditional Comparator (Anonymous Class) Syntax:

```java
import java.util.Comparator;

public class TraditionalComparatorExample {

    public static void main(String[] args) {
        // Creating a comparator for sorting strings in ascending order
        Comparator<String> ascendingComparator = new Comparator<String>() {
            @Override
            public int compare(String str1, String str2) {
                return str1.compareTo(str2);
            }
        };

        // Using the comparator to sort an array of strings
        String[] strings = {"banana", "apple", "orange"};
        Arrays.sort(strings, ascendingComparator);

        // Print the sorted array
        System.out.println("Sorted in ascending order:");
        Arrays.stream(strings).forEach(System.out::println);
    }
}
```

## Comparator Using Lambda Expression:

```java
import java.util.Arrays;
import java.util.Comparator;

public class LambdaComparatorExample {

    public static void main(String[] args) {
        // Creating a comparator for sorting strings in ascending order using lambda expression
        Comparator<String> ascendingComparator = (str1, str2) -> str1.compareTo(str2);

        // Using the comparator to sort an array of strings
        String[] strings = {"banana", "apple", "orange"};
        Arrays.sort(strings, ascendingComparator);

        // Print the sorted array
        System.out.println("Sorted in ascending order:");
        Arrays.stream(strings).forEach(System.out::println);
    }
}
```

### Syntax Explanation:

- **Parameters:** The parameters of the lambda expression are specified in the parentheses `(str1, str2)`.

- **Arrow (->):** The arrow `->` separates the parameters from the body of the lambda expression.

- **Body:** The body of the lambda expression contains the comparison logic, which is the same as the `compare` method in the comparator interface.

## Lambda Expression Shortening:

In the context of comparators, you can further shorten the lambda expression if the comparison is based on a method that already exists in the type being compared. For example, comparing integers:

```java
Comparator<Integer> intComparator = Integer::compare;
```

Here, `Integer::compare` refers to the static `compare` method in the `Integer` class, providing a concise way to create a comparator for integers.

# 5. **Reversed Order and Natural Ordering:**
## Using `Comparator.reverseOrder()` for Reversing the Natural Order:

In Java, the `Comparator.reverseOrder()` method is a convenient way to obtain a comparator that reverses the natural order of elements. This is particularly useful when you want to sort elements in descending order. Here's an example:

```java
import java.util.Arrays;
import java.util.Comparator;

public class ReverseOrderExample {

    public static void main(String[] args) {
        // Sorting integers in descending order using Comparator.reverseOrder()
        Integer[] numbers = {5, 2, 8, 1, 7};
        Arrays.sort(numbers, Comparator.reverseOrder());

        // Print the sorted array in descending order
        System.out.println("Sorted in descending order:");
        Arrays.stream(numbers).forEach(System.out::println);
    }
}
```

In this example, the `Comparator.reverseOrder()` is used to obtain a comparator that sorts integers in descending order. The `Arrays.sort` method then applies this comparator to sort the array of integers.

## Combining Comparators for More Complex Sorting:

Sometimes, you may need to sort elements based on multiple criteria or create more complex sorting logic. The `Comparator` interface provides methods like `thenComparing` to combine comparators. Here's an example:

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;

    // Constructors, getters, setters...

    // Example: Custom Comparator for sorting Persons by age and then by name
    public static Comparator<Person> getAgeAndNameComparator() {
        return Comparator.comparingInt(Person::getAge)
                .thenComparing(Person::getName);
    }
}

public class ComplexSortingExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30),
                new Person("Bob", 25),
                new Person("Charlie", 35),
                new Person("Bob", 28)  // Same name as Bob above but different age
        };

        // Sorting Persons by age and then by name
        Arrays.sort(people, Person.getAgeAndNameComparator());

        // Print the sorted array
        System.out.println("Sorted by age and then by name:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));
    }
}
```

In this example, the `getAgeAndNameComparator` method returns a comparator that first sorts by age in ascending order and then, for elements with the same age, sorts by name in natural order.



# 6. **Null Handling:**
Handling null values in comparators is an important consideration, as nulls can affect the outcome of comparisons and sorting. Here are strategies for handling null values in comparators and an example demonstrating custom null handling logic:

## Strategies for Handling Null Values in Comparators:

1. **Nulls First:**
   - Treat null values as smaller than non-null values. Use `Comparator.nullsFirst()` to create a comparator that considers nulls to be smaller.

2. **Nulls Last:**
   - Treat null values as larger than non-null values. Use `Comparator.nullsLast()` to create a comparator that considers nulls to be larger.

3. **Custom Null Handling Logic:**
   - Implement custom logic to handle null values based on the specific requirements of your application.

## Implementing Custom Null Handling Logic:

```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.Objects;

class Person {
    private String name;
    private Integer age;

    // Constructors, getters, setters...

    // Custom Comparator for sorting Persons by age with custom null handling
    public static Comparator<Person> getAgeComparatorWithNullHandling() {
        return Comparator.comparing(Person::getAge, Comparator.nullsFirst(Integer::compareTo))
                .thenComparing(Objects::requireNonNull, Comparator.naturalOrder());
    }
}

public class NullHandlingExample {

    public static void main(String[] args) {
        // Create an array of Person objects with null values
        Person[] people = {
                new Person("Alice", 30),
                new Person("Bob", null),
                new Person("Charlie", 35),
                new Person("David", null)
        };

        // Sorting Persons by age with custom null handling
        Arrays.sort(people, Person.getAgeComparatorWithNullHandling());

        // Print the sorted array
        System.out.println("Sorted by age with custom null handling:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));
    }
}
```

In this example, the `getAgeComparatorWithNullHandling` method returns a comparator that first sorts by age with nulls considered smaller (`nullsFirst(Integer::compareTo)`) and then, for elements with the same age, sorts by name in natural order (`Comparator.naturalOrder()`).

This approach ensures that null values are handled according to the specified rules while allowing customization of the null handling logic. The `Objects.requireNonNull` is used to enforce non-null values during the comparison. The `thenComparing` method is employed for secondary sorting by name after age.

# 7.  **Chaining Comparators:**
## Combining Multiple Comparators to Achieve Compound Sorting:

Combining multiple comparators allows you to create compound sorting strategies, where elements are first sorted based on one criterion and then, if there are ties, sorted based on another criterion. Java's `Comparator` interface provides the `thenComparing` and `thenComparingInt` methods for this purpose.

## Understanding the `thenComparing` and `thenComparingInt` Methods:

1. **`thenComparing` Method:**
   - The `thenComparing` method is used to create a compound comparator by specifying a secondary comparator.
   - It is typically used after another comparator and is applied when the primary comparator indicates that elements are equal.

2. **`thenComparingInt` Method:**
   - The `thenComparingInt` method is a specialized version of `thenComparing` for primitive `int` values.
   - It avoids the boxing and unboxing overhead associated with using `Integer` objects.

### Example Using `thenComparing`:

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;
    private String city;

    // Constructors, getters, setters...

    // Custom Comparator for compound sorting by age and then by name
    public static Comparator<Person> getAgeAndNameComparator() {
        return Comparator.comparing(Person::getAge)
                .thenComparing(Person::getName);
    }
}

public class CompoundSortingExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30, "New York"),
                new Person("Bob", 25, "London"),
                new Person("Charlie", 35, "Paris"),
                new Person("David", 25, "New York")
        };

        // Sorting Persons by age and then by name
        Arrays.sort(people, Person.getAgeAndNameComparator());

        // Print the sorted array
        System.out.println("Sorted by age and then by name:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old, " + person.getCity()));
    }
}
```

In this example, the `getAgeAndNameComparator` method returns a comparator that first sorts by age in ascending order and then, for elements with the same age, sorts by name in natural order.

### Example Using `thenComparingInt`:

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;
    private String city;

    // Constructors, getters, setters...

    // Custom Comparator for compound sorting by age and then by name length
    public static Comparator<Person> getAgeAndNameLengthComparator() {
        return Comparator.comparing(Person::getAge)
                .thenComparingInt(person -> person.getName().length());
    }
}

public class CompoundSortingExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30, "New York"),
                new Person("Bob", 25, "London"),
                new Person("Charlie", 35, "Paris"),
                new Person("David", 25, "New York")
        };

        // Sorting Persons by age and then by name length
        Arrays.sort(people, Person.getAgeAndNameLengthComparator());

        // Print the sorted array
        System.out.println("Sorted by age and then by name length:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old, " + person.getCity()));
    }
}
```

In this example, the `getAgeAndNameLengthComparator` method returns a comparator that first sorts by age in ascending order and then, for elements with the same age, sorts by the length of the name. The `thenComparingInt` method is used to compare primitive `int` values directly.


# 8.  **Comparing Primitives:**
In Java, the `Comparator` interface provides specialized methods for comparing primitive types directly without the need for boxing and unboxing. These methods are part of the `Comparator` utility class and include `comparingInt`, `comparingDouble`, and `comparingLong`. Using these specialized comparators can improve performance when sorting collections of primitive values. Here's an example demonstrating the usage of these specialized comparators:

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;

    // Constructors, getters, setters...

    // Custom Comparator for sorting Persons by age using comparingInt
    public static Comparator<Person> getAgeComparator() {
        return Comparator.comparingInt(Person::getAge);
    }
}

public class SpecializedComparatorsExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30),
                new Person("Bob", 25),
                new Person("Charlie", 35),
                new Person("David", 25)
        };

        // Sorting Persons by age using comparingInt
        Arrays.sort(people, Person.getAgeComparator());

        // Print the sorted array
        System.out.println("Sorted by age using comparingInt:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));
    }
}
```

In this example, the `getAgeComparator` method returns a comparator that compares `Person` objects based on their age using the `comparingInt` method. This method takes a function that extracts an `int` value from the objects, eliminating the need for boxing `Integer` objects.

Similarly, you can use `comparingDouble` and `comparingLong` for primitive `double` and `long` values, respectively.

```java
// Example for comparing by double value
Comparator<Person> doubleComparator = Comparator.comparingDouble(Person::getDoubleValue);

// Example for comparing by long value
Comparator<Person> longComparator = Comparator.comparingLong(Person::getLongValue);
```

Utilizing these specialized comparators is not only more concise but can also lead to improved performance when working with large datasets of primitive values.

# 9.  **Custom Objects and Comparators:**
When working with custom objects and complex object structures, you might need to implement the `Comparator` interface to define a custom sorting order. Here's an example demonstrating how to create custom objects, implement the `Comparator` interface, and handle complex object structures in comparators:

```java
import java.util.Arrays;
import java.util.Comparator;

class Person {
    private String name;
    private int age;

    // Constructors, getters, setters...

    // Custom Comparator for sorting Persons by age in ascending order
    public static Comparator<Person> getAgeComparator() {
        return Comparator.comparingInt(Person::getAge);
    }

    // Custom Comparator for sorting Persons by name in natural order
    public static Comparator<Person> getNameComparator() {
        return Comparator.comparing(Person::getName);
    }
}

class ComplexPersonComparator implements Comparator<Person> {
    @Override
    public int compare(Person person1, Person person2) {
        // Custom sorting logic based on multiple criteria
        int ageComparison = Integer.compare(person1.getAge(), person2.getAge());
        if (ageComparison != 0) {
            // If ages are different, use age for comparison
            return ageComparison;
        } else {
            // If ages are equal, use name for comparison
            return person1.getName().compareTo(person2.getName());
        }
    }
}

public class CustomSortingExample {

    public static void main(String[] args) {
        // Create an array of Person objects
        Person[] people = {
                new Person("Alice", 30),
                new Person("Bob", 25),
                new Person("Charlie", 35),
                new Person("David", 25)
        };

        // Sorting Persons by age using a custom comparator
        Arrays.sort(people, Person.getAgeComparator());

        // Print the sorted array by age
        System.out.println("Sorted by age:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));

        // Sorting Persons by name using a custom comparator
        Arrays.sort(people, Person.getNameComparator());

        // Print the sorted array by name
        System.out.println("\nSorted by name:");
        Arrays.stream(people).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));

        // Create an array of Person objects with complex sorting criteria
        Person[] peopleWithComplexSort = {
                new Person("Alice", 30),
                new Person("Bob", 25),
                new Person("Charlie", 35),
                new Person("David", 25)
        };

        // Sorting Persons with complex sorting criteria using a custom comparator
        Arrays.sort(peopleWithComplexSort, new ComplexPersonComparator());

        // Print the array sorted by complex criteria
        System.out.println("\nSorted by complex criteria (age then name):");
        Arrays.stream(peopleWithComplexSort).forEach(person ->
                System.out.println(person.getName() + " - " + person.getAge() + " years old"));
    }
}
```

In this example, the `Person` class has two static methods, `getAgeComparator` and `getNameComparator`, that provide comparators for sorting persons by age and name, respectively. Additionally, there is a `ComplexPersonComparator` class implementing the `Comparator` interface to handle complex sorting based on multiple criteria (age and then name). The example demonstrates how to use these comparators to sort an array of `Person` objects based on different criteria. You can adapt and customize the sorting logic according to your specific needs and the complexity of your object structures.

# 10.  **Java 8 Comparator Methods:**
Certainly! Let's create a comprehensive example that utilizes several of the `Comparator` methods to sort a list of custom objects. In this example, we'll have a `Person` class with attributes such as name, age, and city. We'll use different comparators to demonstrate various sorting scenarios:

```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;

class Person {
    private String name;
    private int age;
    private String city;

    public Person(String name, int age, String city) {
        this.name = name;
        this.age = age;
        this.city = city;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public String getCity() {
        return city;
    }

    @Override
    public String toString() {
        return name + " - " + age + " years old, " + city;
    }
}

public class ComparatorExample {

    public static void main(String[] args) {
        // Create a list of Person objects
        List<Person> people = Arrays.asList(
                new Person("Alice", 30, "New York"),
                new Person("Bob", 25, "London"),
                new Person("Charlie", 35, "Paris"),
                new Person("David", 25, "New York")
        );

        // Sorting by age in ascending order
        people.sort(Comparator.comparingInt(Person::getAge));
        System.out.println("Sorted by age in ascending order:");
        people.forEach(System.out::println);

        System.out.println("\n-----------------------------");

        // Sorting by age in descending order using reversed()
        people.sort(Comparator.comparingInt(Person::getAge).reversed());
        System.out.println("Sorted by age in descending order:");
        people.forEach(System.out::println);

        System.out.println("\n-----------------------------");

        // Sorting by age, then by name in natural order
        people.sort(Comparator.comparingInt(Person::getAge).thenComparing(Person::getName));
        System.out.println("Sorted by age, then by name:");
        people.forEach(System.out::println);

        System.out.println("\n-----------------------------");

        // Sorting by city length, nulls first
        people.sort(
                Comparator.comparing(Person::getCity, Comparator.nullsFirst(Comparator.comparingInt(String::length)))
        );
        System.out.println("Sorted by city length, nulls first:");
        people.forEach(System.out::println);
    }
}
```

In this example, we create a list of `Person` objects and demonstrate the following:

1. Sorting by age in ascending order using `Comparator.comparingInt`.
2. Sorting by age in descending order using `Comparator.comparingInt().reversed()`.
3. Sorting by age, then by name in natural order using `Comparator.comparingInt().thenComparing`.
4. Sorting by city length, with nulls first using `Comparator.comparing().nullsFirst()`.

8.  **Comparing Streams:**
    - Sorting elements in streams using comparators.
    - Applying comparators in stream operations.

9.  **Performance Considerations:**
    - Understanding the performance implications of using different comparison strategies.
    - Discussing the time complexity of sorting algorithms.

10. **Case Studies and Real-World Examples:**
    - Analyzing real-world scenarios where comparators are beneficial.
    - Discussing examples from popular Java libraries and frameworks.

11. **Advanced Topics (Optional):**
    - Exploring advanced topics such as custom comparators with dynamic behavior.
    - Using comparators in concurrent environments.