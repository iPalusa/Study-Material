### 1. Implement a program to check if a string is a palindrome.
```py
def is_palindrome(s):
    # Remove spaces and convert to lowercase for case-insensitive comparison
    cleaned_string = ''.join(s.split()).lower()

    # Compare the original string with its reverse
    return cleaned_string == cleaned_string[::-1]

# Example usage
input_string = "A man a plan a canal Panama"
if is_palindrome(input_string):
    print(f"'{input_string}' is a palindrome.")
else:
    print(f"'{input_string}' is not a palindrome.")
```
### 2. Create a program to calculate the area of a circle
```py
import math

def calculate_circle_area(radius):
    if radius < 0:
        return "Radius cannot be negative."
    else:
        area = math.pi * (radius ** 2)
        return area

# Example usage
radius = float(input("Enter the radius of the circle: "))
result = calculate_circle_area(radius)

if isinstance(result, str):
    print(result)
else:
    print(f"The area of the circle with radius {radius} is: {result:.2f}")
```
### 3. Create a program to find the largest element in an array
```py
def find_largest_element(arr):
    if not arr:
        return "Array is empty."
    
    largest_element = arr[0]

    for element in arr:
        if element > largest_element:
            largest_element = element

    return largest_element

# Example usage
input_array = [5, 12, 3, 8, 15, 7, 10]
result = find_largest_element(input_array)

if isinstance(result, str):
    print(result)
else:
    print(f"The largest element in the array is: {result}")
```
### 4. Write a program to check if two strings are anagrams
```py
def are_anagrams(str1, str2):
    # Remove spaces and convert to lowercase for case-insensitive comparison
    cleaned_str1 = ''.join(str1.split()).lower()
    cleaned_str2 = ''.join(str2.split()).lower()

    # Check if the sorted characters of both strings are the same
    return sorted(cleaned_str1) == sorted(cleaned_str2)

# Example usage
string1 = "Listen"
string2 = "Silent"

if are_anagrams(string1, string2):
    print(f"'{string1}' and '{string2}' are anagrams.")
else:
    print(f"'{string1}' and '{string2}' are not anagrams.")
```
### 5. Create a program to generate random numbers within a range.
```py
import random

def generate_random_number(start, end):
    if start > end:
        return "Invalid range. Start value should be less than or equal to end value."
    else:
        return random.randint(start, end)

# Example usage
start_range = int(input("Enter the start of the range: "))
end_range = int(input("Enter the end of the range: "))

random_number = generate_random_number(start_range, end_range)

if isinstance(random_number, str):
    print(random_number)
else:
    print(f"Random number within the range [{start_range}, {end_range}]: {random_number}")
```

### 6. Implement a program to count the number of vowels and consonants in a string
```python
def count_vowels_and_consonants(input_string):
    # Define a set of vowels
    vowels = set("aeiouAEIOU")

    # Initialize counters
    vowel_count = 0
    consonant_count = 0

    # Iterate through each character in the input string
    for char in input_string:
        # Check if the character is an alphabet
        if char.isalpha():
            # Check if the character is a vowel
            if char in vowels:
                vowel_count += 1
            else:
                consonant_count += 1

    return vowel_count, consonant_count

# Get input from the user
user_input = input("Enter a string: ")

# Call the function to count vowels and consonants
vowels, consonants = count_vowels_and_consonants(user_input)

# Display the results
print("Number of vowels:", vowels)
print("Number of consonants:", consonants)
```
### 7. Create a program to remove duplicate elements from an array
```py
def remove_duplicates(input_array):
    # Use a set to convert the array to a set (removing duplicates)
    unique_set = set(input_array)

    # Convert the set back to a list to maintain the order
    unique_list = list(unique_set)

    return unique_list

# Example usage:
input_array = [1, 2, 3, 4, 2, 5, 6, 1]
result = remove_duplicates(input_array)

print("Original Array:", input_array)
print("Array with Duplicates Removed:", result)
```
### 8. 