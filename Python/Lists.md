# 1. Basics

### **1. Introduction to Lists:**
   - Lists are ordered, mutable collections of elements.
   - Elements can be of different data types.
  
   ```python
   my_list = [1, 2, 3, 'hello', True]
   ```

### **2. Creating Lists:**
   - Use square brackets `[]` to create a list.
   - Elements can be of any data type.

   ```python
   numbers = [1, 2, 3, 4, 5]
   names = ['Alice', 'Bob', 'Charlie']
   ```

### **3. Accessing List Elements:**
   - Use index to access elements (indexing starts at 0).

   ```python
   first_element = my_list[0]
   third_element = numbers[2]
   ```

### **4. List Operations (Concatenation, Repetition):**
   - Concatenate lists using `+`.

   ```python
   combined_list = numbers + names
   ```

   - Repeat a list using `*`.

   ```python
   repeated_list = numbers * 3
   ```

### **5. Indexing and Slicing:**
   - Use positive and negative indices.
   - Slicing with `start:stop:step`.

   ```python
   # Positive Indexing
   first_element = numbers[0]

   # Negative Indexing
   last_element = numbers[-1]

   # Slicing
   sub_list = numbers[1:4]
   ```

# 2. List Methods

### **1. `append()` - Add an element to the end of the list:**
```python
numbers = [1, 2, 3]
numbers.append(4)
print(numbers)  # Output: [1, 2, 3, 4]
```

### **2. `extend()` - Add elements from another iterable to the end:**
```python
fruits = ['apple', 'banana']
more_fruits = ['orange', 'grape']
fruits.extend(more_fruits)
print(fruits)  # Output: ['apple', 'banana', 'orange', 'grape']
```

### **3. `insert()` - Insert an element at a specified position:**
```python
colors = ['red', 'blue', 'green']
colors.insert(1, 'yellow')
print(colors)  # Output: ['red', 'yellow', 'blue', 'green']
```

### **4. `remove()` - Remove the first occurrence of a value:**
```python
animals = ['dog', 'cat', 'rabbit', 'cat']
animals.remove('cat')
print(animals)  # Output: ['dog', 'rabbit', 'cat']
```

### **5. `pop()` - Remove and return an element by index (default last):**
```python
numbers = [10, 20, 30, 40]
removed = numbers.pop(1)
print(numbers)  # Output: [10, 30, 40]
print(removed)  # Output: 20
```

### **6. `clear()` - Remove all elements from the list:**
```python
letters = ['a', 'b', 'c']
letters.clear()
print(letters)  # Output: []
```

### **7. `index()` - Return the index of the first occurrence of a value:**
```python
numbers = [5, 10, 15, 20]
index = numbers.index(15)
print(index)  # Output: 2
```

### **8. `count()` - Count the number of occurrences of a value:**
```python
numbers = [1, 2, 3, 2, 4, 2, 5]
count = numbers.count(2)
print(count)  # Output: 3
```

### **9. `sort()` - Sort the list in ascending order (in-place):**
```python
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()
print(numbers)  # Output: [1, 1, 2, 3, 4, 5, 9]
```

### **10. `reverse()` - Reverse the elements of the list (in-place):**
```python
letters = ['a', 'b', 'c']
letters.reverse()
print(letters)  # Output: ['c', 'b', 'a']
```
# 3. List Comprehensions

### **List Comprehension Basics:**
```python
# Basic syntax
new_list = [expression for item in iterable]

# Example: Create a list of squares
squares = [x**2 for x in range(5)]
# Output: [0, 1, 4, 9, 16]
```

### **Conditionals in List Comprehensions:**
```python
# List comprehension with if condition
new_list = [expression for item in iterable if condition]

# Example: Create a list of even numbers
evens = [x for x in range(10) if x % 2 == 0]
# Output: [0, 2, 4, 6, 8]
```

### **Conditionals - If-Else in List Comprehensions:**
```python
# List comprehension with if-else condition
new_list = [true_expr if condition else false_expr for item in iterable]

# Example: Create a list of even or odd labels
labels = ['Even' if x % 2 == 0 else 'Odd' for x in range(5)]
# Output: ['Even', 'Odd', 'Even', 'Odd', 'Even']
```

### **Nested List Comprehensions:**
```python
# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for row in matrix for num in row]
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### **Nested List Comprehensions with Conditionals:**
```python
# Nested list comprehension with condition
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
even_numbers = [num for row in matrix for num in row if num % 2 == 0]
# Output: [2, 4, 6, 8]
```

### **Multiple Conditions in List Comprehensions:**
```python
# List comprehension with multiple conditions
new_list = [expression for item in iterable if condition1 and condition2]

# Example: Create a list of numbers divisible by 2 and 3
divisible_by_2_and_3 = [x for x in range(20) if x % 2 == 0 and x % 3 == 0]
# Output: [0, 6, 12, 18]
```
# 4. Working with nested lists

### **Accessing and Modifying Elements in Nested Lists:**

#### Accessing Elements:
```python
# Nested List
nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# Accessing an element
element_1_2 = nested_list[1][2]
print(element_1_2)  # Output: 6

# Accessing a sub-list
sub_list = nested_list[0]
print(sub_list)  # Output: [1, 2, 3]
```

#### Modifying Elements:
```python
# Modifying an element
nested_list[1][2] = 10
print(nested_list)
# Output: [[1, 2, 3], [4, 5, 10], [7, 8, 9]]

# Modifying a sub-list
nested_list[0] = [11, 12, 13]
print(nested_list)
# Output: [[11, 12, 13], [4, 5, 10], [7, 8, 9]]
```

### **Nested List Comprehensions:**

#### Creating a Flat List from Nested List:
```python
nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

flat_list = [num for sublist in nested_list for num in sublist]
print(flat_list)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### Creating a Transposed Matrix:
```python
nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

transposed = [[row[i] for row in nested_list] for i in range(len(nested_list[0]))]
print(transposed)
# Output: [[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```

#### Filtering Elements in Nested List:
```python
nested_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

filtered_list = [num for sublist in nested_list for num in sublist if num % 2 == 0]
print(filtered_list)
# Output: [2, 4, 6, 8]
```
# 5. Common operations and patterns

### **1. Finding the Length of a List:**
```python
my_list = [1, 2, 3, 4, 5]
length = len(my_list)
print("Length of the list:", length)
```

### **2. Checking for the Existence of an Element:**
```python
my_list = [1, 2, 3, 4, 5]
element_to_check = 3

if element_to_check in my_list:
    print(f"{element_to_check} exists in the list.")
else:
    print(f"{element_to_check} does not exist in the list.")
```

### **3. Concatenating Lists:**
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
concatenated_list = list1 + list2
print("Concatenated List:", concatenated_list)
```

### **4. Reversing a List:**
```python
my_list = [1, 2, 3, 4, 5]
reversed_list = list(reversed(my_list))
print("Reversed List:", reversed_list)
```

### **5. Copying a List:**
```python
original_list = [1, 2, 3]
# Shallow Copy
shallow_copy = original_list.copy()
# Deep Copy (requires the copy module)
import copy
deep_copy = copy.deepcopy(original_list)

print("Original List:", original_list)
print("Shallow Copy:", shallow_copy)
print("Deep Copy:", deep_copy)
```

### **6. Slicing Techniques:**
```python
my_list = [1, 2, 3, 4, 5]

# Get elements from index 1 to 3 (exclusive)
slice1 = my_list[1:3]

# Get all elements from index 2 to the end
slice2 = my_list[2:]

# Get all elements up to index 3 (exclusive)
slice3 = my_list[:3]

# Get the last two elements
slice4 = my_list[-2:]

print("Slice 1:", slice1)
print("Slice 2:", slice2)
print("Slice 3:", slice3)
print("Slice 4:", slice4)
```

# 6. List Iteration and Looping

### **1. Using `for` Loops with Lists:**

#### Basic Iteration:
```python
fruits = ['apple', 'banana', 'orange']

for fruit in fruits:
    print(fruit)
```

#### Iterating with Index:
```python
for i in range(len(fruits)):
    print(fruits[i])
```

### **2. Iterating with `enumerate()`:**

#### Basic `enumerate()` Usage:
```python
for index, value in enumerate(fruits):
    print(f"Index: {index}, Value: {value}")
```

#### Specifying Start Index for `enumerate()`:
```python
for index, value in enumerate(fruits, start=1):
    print(f"Index: {index}, Value: {value}")
```

### **3. Using `zip()` with Lists:**

#### Basic `zip()` Usage:
```python
names = ['Alice', 'Bob', 'Charlie']

for fruit, name in zip(fruits, names):
    print(f"{name} likes {fruit}")
```

#### Handling Lists of Unequal Length:
```python
colors = ['red', 'green']

for fruit, color, name in zip(fruits, colors, names):
    print(f"{name} likes {color} {fruit}")
```

#### Unzipping a List of Tuples:
```python
combined = list(zip(fruits, names))
unzipped_fruits, unzipped_names = zip(*combined)
```

# 7. List Comprehension and Lamda Functions

### **Combining List Comprehensions with Functions:**
1. **Using a Function to Modify Elements:**
   ```python
   def square(x):
       return x ** 2

   # Using list comprehension to apply the function to each element
   squared_numbers = [square(x) for x in range(1, 6)]
   # Result: [1, 4, 9, 16, 25]
   ```

2. **Filtering with a Function:**
   ```python
   def is_even(x):
       return x % 2 == 0

   # Using list comprehension to filter elements based on the function
   even_numbers = [x for x in range(1, 11) if is_even(x)]
   # Result: [2, 4, 6, 8, 10]
   ```

### **Using Lambda Functions with Lists:**
1. **Basic Lambda Function:**
   ```python
   # Lambda function to square a number
   square = lambda x: x ** 2

   # Using the lambda function in a list comprehension
   squared_numbers = [square(x) for x in range(1, 6)]
   # Result: [1, 4, 9, 16, 25]
   ```

2. **Lambda Function for Filtering:**
   ```python
   # Lambda function to check if a number is even
   is_even = lambda x: x % 2 == 0

   # Using the lambda function for filtering in a list comprehension
   even_numbers = [x for x in range(1, 11) if is_even(x)]
   # Result: [2, 4, 6, 8, 10]
   ```

3. **Lambda Function with Map:**
   ```python
   # Lambda function to double each element
   double = lambda x: x * 2

   # Using the lambda function with map
   doubled_numbers = list(map(double, [1, 2, 3, 4, 5]))
   # Result: [2, 4, 6, 8, 10]
   ```

4. **Lambda Function with Filter:**
   ```python
   # Lambda function to filter even numbers
   is_even = lambda x: x % 2 == 0

   # Using the lambda function with filter
   even_numbers = list(filter(is_even, [1, 2, 3, 4, 5]))
   # Result: [2, 4]
   ```
# 8. Sorting and Searching in Lists

### **Sorting Lists:**
#### In-Place Sorting:
```python
numbers = [4, 2, 7, 1, 9]
numbers.sort()
print(numbers)
# Output: [1, 2, 4, 7, 9]
```

#### Using `sorted()` for a New Sorted List:
```python
numbers = [4, 2, 7, 1, 9]
sorted_numbers = sorted(numbers)
print(sorted_numbers)
# Output: [1, 2, 4, 7, 9]
```

### **Custom Sorting with `key` Parameter:**
```python
# Sorting a list of tuples based on the second element
pairs = [(1, 3), (2, 1), (4, 0), (1, 2)]
sorted_pairs = sorted(pairs, key=lambda x: x[1])
print(sorted_pairs)
# Output: [(4, 0), (2, 1), (1, 2), (1, 3)]
```

### **Binary Search in Lists:**
#### Using `bisect_left` for Binary Search:
```python
from bisect import bisect_left

numbers = [1, 2, 4, 7, 9]
index = bisect_left(numbers, 4)
print(index)
# Output: 2 (index where 4 should be inserted to maintain sorted order)
```

#### Binary Search with Custom Sorting:
```python
from bisect import bisect_left

pairs = [(1, 3), (2, 1), (4, 0), (1, 2)]
sorted_pairs = sorted(pairs, key=lambda x: x[1])

# Binary search based on the second element of the tuples
index = bisect_left(sorted_pairs, (2, 0), key=lambda x: x[1])
print(index)
# Output: 2 (index where (2, 0) should be inserted to maintain sorted order)
```

# 9. Advanced

### **Shallow Copy vs. Deep Copy:**
#### Shallow Copy:
```python
import copy

original_list = [1, [2, 3], 4]
shallow_copy = copy.copy(original_list)

# Modify the copied list
shallow_copy[1][0] = 'X'

print(original_list)  # [1, ['X', 3], 4]
```

#### Deep Copy:
```python
import copy

original_list = [1, [2, 3], 4]
deep_copy = copy.deepcopy(original_list)

# Modify the copied list
deep_copy[1][0] = 'Y'

print(original_list)  # [1, [2, 3], 4]
```

### **List Memory Management:**
#### Memory Usage:
```python
import sys

my_list = [1, 2, 3, 4, 5]

# Size of the list in bytes
print(sys.getsizeof(my_list))
```

### **Performance Considerations with Large Lists:**
#### Timing List Operations:
```python
import time

start_time = time.time()

# Code with list operations

end_time = time.time()
elapsed_time = end_time - start_time
print(f"Elapsed Time: {elapsed_time} seconds")
```

#### Using Generators for Large Lists:
```python
# Instead of creating a large list, use a generator
large_list_generator = (x for x in range(10**6))

# Process elements on-the-fly without loading the entire list into memory
for element in large_list_generator:
    # Process each element
    pass
```

#### Memory Views for Large Data:
```python
# Use memory views for large lists or arrays
data = [0, 1, 2, 3, 4]
memory_view = memoryview(data)

# Access and manipulate elements efficiently
print(memory_view[1])  # 1
memory_view[1] = 10
print(data)  # [0, 10, 2, 3, 4]
```

# 10.Error Handling


### **Handling Index Errors:**
1. **Check if the index is within bounds:**
   ```python
   my_list = [1, 2, 3, 4, 5]
   index_to_check = 7

   if 0 <= index_to_check < len(my_list):
       print(my_list[index_to_check])
   else:
       print("Index out of bounds.")
   ```

2. **Use try-except block for safer access:**
   ```python
   my_list = [1, 2, 3, 4, 5]
   index_to_check = 7

   try:
       value = my_list[index_to_check]
       print(value)
   except IndexError:
       print("Index out of bounds.")
   ```

### **Dealing with Empty Lists:**
1. **Check if the list is empty before accessing elements:**
   ```python
   my_list = []

   if not my_list:
       print("List is empty.")
   else:
       print(my_list[0])
   ```

2. **Use a default value or handle with try-except for safer access:**
   ```python
   my_list = []

   # Option 1: Using a default value
   first_element = my_list[0] if my_list else None
   print(first_element)

   # Option 2: Using try-except
   try:
       first_element = my_list[0]
       print(first_element)
   except IndexError:
       print("List is empty.")
   ```

3. **Safely iterate over an empty list:**
   ```python
   my_list = []

   for element in my_list:
       print(element)
   else:
       print("List is empty.")
   ```
