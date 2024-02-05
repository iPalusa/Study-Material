# 1. Introduction
---
- They are used to organize a collection of data elements into a specific order.
- when dealing with large amounts of data, manual sorting can be impractical and time-consuming. This is where computer algorithms come in.
- Sorting algorithms are designed to automatically sort large amounts of data in an efficient and reliable way.
- Common examples of sorting algorithms include Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort, and Heap Sort.

# 2. Difference between sorting Algorithms
---
Sure, here's a comparison between various sorting algorithms:

1. Bubble Sort
- Simple and easy to understand
- Inefficient for large datasets
- Time complexity: O(n^2)
- Space complexity: O(1)
- Stable sort

2. Selection Sort
- Simple and easy to understand
- Inefficient for large datasets
- Time complexity: O(n^2)
- Space complexity: O(1)
- Unstable sort

3. Insertion Sort
- Efficient for small datasets and almost-sorted datasets
- Inefficient for large datasets
- Time complexity: O(n^2)
- Space complexity: O(1)
- Stable sort

4. Merge Sort
- Efficient for large datasets
- Time complexity: O(n log n)
- Space complexity: O(n)
- Stable sort

5. Quick Sort
- Efficient for large datasets
- Average time complexity: O(n log n)
- Worst-case time complexity: O(n^2)
- Space complexity: O(log n)
- Unstable sort

6. Heap Sort
- Efficient for large datasets
- Time complexity: O(n log n)
- Space complexity: O(1)
- Unstable sort


# 3. Bubble Sort
---

## 3.1 Merits and Demerits of Bubble Sort

| Advantages                  | Disadvantages                          |
|-----------------------------|----------------------------------------|
| Simple and easy to implement| Inefficient for large datasets         |
| Efficient for small datasets| Time complexity: O(n^2)                |
| Easy to understand          | Space complexity: O(1)                 |
| Stable sort                 | Not suitable for real-time applications|

## 3.2 Time and Space Complexity

**Time complexity:** Bubble Sort has a time complexity of O(n^2), where n is the number of elements in the array. This means that the time taken to sort an array using Bubble Sort increases quadratically with the size of the array. For very large arrays, Bubble Sort can be very slow and inefficient, which is why it's generally not used for large datasets.

**Space complexity:** Bubble Sort has a space complexity of O(1), which means that it doesn't require any additional memory space beyond the original array. This is because Bubble Sort sorts the array in place, by swapping adjacent elements if they're in the wrong order. This can be an advantage in situations where memory is limited, but it also means that Bubble Sort can't be easily parallelized or optimized for memory usage.

## 3.3 Bubble Sort 

- Bubble Sort is a simple sorting algorithm that works by repeatedly swapping adjacent elements in a list or array, if they're in the wrong order.

## 3.4 Adaptive Bubble Sort

- Adaptive Bubble Sort is a variation of the Bubble Sort algorithm that takes advantage of the fact that some portions of the array may already be sorted to reduce the number of iterations required for sorting the array.
- After each pass, the algorithm checks if any swaps were made. If no swaps were made, then the array must already be sorted, and the algorithm stops. Otherwise, the algorithm continues with the next pass as usual.
- the worst-case time complexity of the Adaptive Bubble Sort algorithm is still O(n^2), which means that it can be inefficient for large arrays or for arrays that are not already sorted.

### Examples
#### 1. Array Partition I
Given an array of 2n integers, your task is to group these integers into n pairs, such that the sum of the minimum of each pair is maximized.

**Example:** Input: [1,4,3,2] Output: 4

**Explanation:** The minimum values of the pairs are (1, 2) and (3, 4). Therefore, the sum of the minimum values is 1 + 3 = 4.
```python
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        n = len(nums)
        swapped = True
        i = 0
        while swapped:
            swapped = False
            for j in range(n-i-1):
                if nums[j] > nums[j+1]:
                    nums[j], nums[j+1] = nums[j+1], nums[j]
                    swapped = True
            i += 1
        sum = 0
        for i in range(0, n, 2):
            sum += nums[i]
        return sum
```