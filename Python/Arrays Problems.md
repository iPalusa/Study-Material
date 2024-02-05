### 1. Rotate the elements of an array to the right by a given number of positions
```py
def rotate_array(arr, positions):
    n = len(arr)
    positions = positions % n  # Ensure positions is within the array size
    
    # Rotate the array using slicing
    rotated_array = arr[-positions:] + arr[:-positions]

    return rotated_array

# Example usage:
original_array = [1, 2, 3, 4, 5]
positions_to_rotate = 2

result = rotate_array(original_array, positions_to_rotate)
print("Original Array: ", original_array)
print("Rotated Array: ", result)

""" Original Array: [1, 2, 3, 4, 5]
Rotated Array: [4, 5, 1, 2, 3] """
```