# 1. Basics

### Definition:
A set is an unordered collection of unique elements.

#### Characteristics:
**Uniqueness:** Elements in a set are unique; duplicates are not allowed.

**Unordered:** Elements have no specific order.

**Mutable (Changeable):** You can add or remove elements from a set.

**No Indexing:** Sets do not support indexing or slicing like lists.


### 1. Using Curly Braces `{}`:
```python
# Creating a set with elements
my_set = {1, 2, 3, 4, 5}
print(my_set)

# Creating an empty set
empty_set = set()
print(empty_set)

# Note: If you want to create an empty dictionary, you should use empty curly braces like this: {}
```

### 2. Using `set()` Constructor:
```python
# Creating a set with elements
my_set = set([1, 2, 3, 4, 5])
print(my_set)

# Creating an empty set
empty_set = set()
print(empty_set)
```

**Note:**
- When using curly braces `{}` to create a set, ensure that there is at least one element inside, as an empty pair of curly braces `{}` is used for creating an empty dictionary.

- The `set()` constructor can take an iterable (like a list) as an argument to initialize the set. It can also be used to convert other iterable types (lists, tuples, strings) into sets.