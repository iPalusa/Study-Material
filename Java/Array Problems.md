## 1. Rotate the elements of an array to the right by a given number of positions
```java
public class ArrayRotation {
    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};
        int positionsToRotate = 2;

        System.out.println("Original Array: " + java.util.Arrays.toString(array));

        rotateArrayRight(array, positionsToRotate);

        System.out.println("Array after rotation: " + java.util.Arrays.toString(array));
    }

    public static void rotateArrayRight(int[] arr, int positions) {
        if (arr == null || arr.length == 0) {
            return; // Nothing to rotate
        }
 
        int length = arr.length;
        positions = positions % length; // In case positions are greater than array length 

        // Create a temporary array to store the rotated elements
        int[] temp = new int[length];

        // Copy the elements to the temporary array with rotation
        for (int i = 0; i < length; i++) {
            temp[(i + positions) % length] = arr[i];
        }

        // Copy the rotated elements back to the original array
        System.arraycopy(temp, 0, arr, 0, length);
    }
}
// Original Array: [1, 2, 3, 4, 5]
// Array after rotation: [4, 5, 1, 2, 3]
// temp[(0 + 2) % 5] = 1;  // temp[2] = 1
// temp[(1 + 2) % 5] = 2;  // temp[3] = 2
// temp[(2 + 2) % 5] = 3;  // temp[4] = 3
// temp[(3 + 2) % 5] = 4;  // temp[0] = 4
// temp[(4 + 2) % 5] = 5;  // temp[1] = 5

```

## 2.Write a function to remove duplicate elements from an array.
```java
import java.util.Arrays;
import java.util.LinkedHashSet;

public class RemoveDuplicates {
    public static void main(String[] args) {
        int[] array = {1, 2, 2, 3, 4, 4, 5};
        System.out.println("Original Array: " + Arrays.toString(array));

        int[] result = removeDuplicates(array);

        System.out.println("Array after removing duplicates: " + Arrays.toString(result));
    }

    public static int[] removeDuplicates(int[] arr) {
        // Using LinkedHashSet to automatically remove duplicates while preserving order
        LinkedHashSet<Integer> set = new LinkedHashSet<>();

        // Adding elements to the set to remove duplicates
        for (int value : arr) {
            set.add(value);
        }

        // Converting the set back to an array
        int[] result = new int[set.size()];
        int index = 0;
        for (int value : set) {
            result[index++] = value;
        }

        return result;
    }
}
```
## 3. Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing.
```java
public class MissingNumber {
    public static void main(String[] args) {
        int[] array = {3, 0, 1}; // Example array, missing number is 2
        int missingNumber = findMissingNumber(array);
        System.out.println("Missing Number: " + missingNumber);
    }

    public static int findMissingNumber(int[] nums) {
        int n = nums.length;
        int expectedSum = n * (n + 1) / 2;
        int actualSum = 0;

        for (int num : nums) {
            actualSum += num;
        }

        return expectedSum - actualSum;
    }
}
```
## 4. Given an array where all elements occur even times except one, find the element occurring odd times.
```java
public class OddOccurrence {
    public static void main(String[] args) {
        int[] array = {4, 2, 1, 2, 1, 4, 3}; // Example array, the element occurring odd times is 3
        int oddOccurrence = findOddOccurrence(array);
        System.out.println("Element occurring odd times: " + oddOccurrence);
    }

    public static int findOddOccurrence(int[] nums) {
        int result = 0;

        for (int num : nums) {
            result ^= num;
        }

        return result;
    }
}
```
## 5. Merge two sorted arrays into a single sorted array.
```java
public class MergeSortedArrays {
    public static void main(String[] args) {
        int[] array1 = {1, 3, 5, 7, 9};
        int[] array2 = {2, 4, 6, 8, 10};
        
        int[] mergedArray = mergeSortedArrays(array1, array2);

        System.out.println("Merged Array: " + java.util.Arrays.toString(mergedArray));
    }

    public static int[] mergeSortedArrays(int[] array1, int[] array2) {
        int length1 = array1.length;
        int length2 = array2.length;
        int[] mergedArray = new int[length1 + length2];

        int i = 0, j = 0, k = 0;

        while (i < length1 && j < length2) {
            if (array1[i] < array2[j]) {
                mergedArray[k++] = array1[i++];
            } else {
                mergedArray[k++] = array2[j++];
            }
        }

        // Copy remaining elements from both arrays, if any
        while (i < length1) {
            mergedArray[k++] = array1[i++];
        }

        while (j < length2) {
            mergedArray[k++] = array2[j++];
        }

        return mergedArray;
    }
}
```
## 6. Write a function to find common elements between two arrays.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class CommonElementsFinder {

    public static void main(String[] args) {
        int[] array1 = {1, 2, 3, 4, 5};
        int[] array2 = {3, 4, 5, 6, 7};

        int[] commonElements = findCommonElements(array1, array2);

        System.out.println("Common Elements: " + Arrays.toString(commonElements));
    }

    public static int[] findCommonElements(int[] array1, int[] array2) {
        Set<Integer> set = new HashSet<>();
        List<Integer> commonList = new ArrayList<>();

        for (int num : array1) {
            set.add(num);
        }

        for (int num : array2) {
            if (set.contains(num)) {
                commonList.add(num);
            }
        }

        // Convert List to array
        int[] commonElements = new int[commonList.size()];
        for (int i = 0; i < commonList.size(); i++) {
            commonElements[i] = commonList.get(i);
        }

        return commonElements;
    }
}
```
## 7. An element is a leader if it is greater than or equal to all elements to its right. Find all leaders in an array.
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class LeadersInArray {

    public static void main(String[] args) {
        int[] array = {16, 17, 4, 3, 5, 2};

        List<Integer> leaders = findLeaders(array);

        System.out.println("Leaders in the array: " + leaders);
    }

    public static List<Integer> findLeaders(int[] array) {
        List<Integer> leaders = new ArrayList<>();

        // Initialize the maximum element to be the last element of the array
        int maxRight = array[array.length - 1];

        // The last element is always a leader
        leaders.add(maxRight);

        // Iterate from the second-to-last element to the first element
        for (int i = array.length - 2; i >= 0; i--) {
            // If the current element is greater than or equal to the maxRight
            if (array[i] >= maxRight) {
                // Update the maxRight to the current element
                maxRight = array[i];
                // Add the current element to the list of leaders
                leaders.add(array[i]);
            }
        }

        // Reverse the list to get the leaders in the correct order
        Collections.reverse(leaders);

        return leaders;
    }
}
```
## 8.  Write a function to move all zeros to the end of an array without changing the order of non-zero elements.
```java
public class MoveZerosToEnd {

    public static void moveZerosToEnd(int[] array) {
        int nonZeroIndex = 0;

        // Traverse the array and move non-zero elements to the front
        for (int i = 0; i < array.length; i++) {
            if (array[i] != 0) {
                // Swap non-zero element with the element at nonZeroIndex
                int temp = array[i];
                array[i] = array[nonZeroIndex];
                array[nonZeroIndex] = temp;

                // Increment nonZeroIndex
                nonZeroIndex++;
            }
        }
    }

    public static void main(String[] args) {
        int[] array = {1, 0, 3, 0, 5, 0, 12};

        System.out.println("Original Array: " + Arrays.toString(array));

        moveZerosToEnd(array);

        System.out.println("Array after moving zeros to the end: " + Arrays.toString(array));
    }
}
```
### or
```java
public class MoveZerosToEnd {

    public static void moveZerosToEnd(int[] arr) {
        int n = arr.length;
        int count = 0; // Count of non-zero elements

        // Traverse the array and move non-zero elements to the front
        for (int i = 0; i < n; i++) {
            if (arr[i] != 0) {
                arr[count++] = arr[i];
            }
        }

        // Fill the remaining positions with zeros
        while (count < n) {
            arr[count++] = 0;
        }
    }

    public static void main(String[] args) {
        int[] array = {1, 0, 2, 0, 3, 4, 0, 5};
        
        System.out.println("Original Array: " + Arrays.toString(array));
        
        moveZerosToEnd(array);

        System.out.println("Array after moving zeros to the end: " + Arrays.toString(array));
    }
}
```
## 9.  Find the intersection of two arrays.
```java
import java.util.Arrays;
import java.util.HashSet;
import java.util.Set;

public class ArrayIntersection {

    public static int[] findIntersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> resultSet = new HashSet<>();

        // Add elements of the first array to the set
        for (int num : nums1) {
            set1.add(num);
        }

        // Check for intersection while iterating through the second array
        for (int num : nums2) {
            if (set1.contains(num)) {
                resultSet.add(num);
            }
        }

        // Convert set to array
        int[] resultArray = new int[resultSet.size()];
        int index = 0;
        for (int num : resultSet) {
            resultArray[index++] = num;
        }

        return resultArray;
    }

    public static void main(String[] args) {
        int[] array1 = {1, 2, 2, 1};
        int[] array2 = {2, 2};

        int[] intersection = findIntersection(array1, array2);

        System.out.println("Intersection of arrays: " + Arrays.toString(intersection));
    }
}
```

## 10. Write a function to randomly shuffle the elements of an array.
```java
import java.util.Random;

public class ArrayShuffle {

    public static void shuffleArray(int[] arr) {
        Random rand = new Random();

        for (int i = arr.length - 1; i > 0; i--) {
            // Generate a random index between 0 and i (inclusive)
            int j = rand.nextInt(i + 1);

            // Swap arr[i] and arr[j]
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }

    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};

        System.out.println("Original Array: " + Arrays.toString(array));

        shuffleArray(array);

        System.out.println("Shuffled Array: " + Arrays.toString(array));
    }
}
```

## 11. Create a new array where each element is the product of all elements in the original array except the one at that index.
```java
import java.util.Arrays;

public class ProductExceptSelf {

    public static int[] productExceptSelf(int[] nums) {
        int n = nums.length;

        // Initialize two arrays to store the product of elements to the left and right of each index
        int[] leftProducts = new int[n];
        int[] rightProducts = new int[n];

        // Initialize the result array
        int[] result = new int[n];

        // Calculate the product of elements to the left of each index
        int leftProduct = 1;
        for (int i = 0; i < n; i++) {
            leftProducts[i] = leftProduct;
            leftProduct *= nums[i];
        }

        // Calculate the product of elements to the right of each index
        int rightProduct = 1;
        for (int i = n - 1; i >= 0; i--) {
            rightProducts[i] = rightProduct;
            rightProduct *= nums[i];
        }

        // Calculate the product for each index by multiplying left and right products
        for (int i = 0; i < n; i++) {
            result[i] = leftProducts[i] * rightProducts[i];
        }

        return result;
    }

    public static void main(String[] args) {
        int[] originalArray = {1, 2, 3, 4};

        System.out.println("Original Array: " + Arrays.toString(originalArray));

        int[] resultArray = productExceptSelf(originalArray);

        System.out.println("Result Array: " + Arrays.toString(resultArray));
    }
}
```
## 12. Find the peak element in an array (an element which is greater than or equal to its neighbors).
```java
public class PeakElementFinder {

    // Function to find a peak element in an array
    public static int findPeakElement(int[] nums) {
        int n = nums.length;

        // Edge cases
        if (n == 1) {
            return 0; // There is only one element, and it is a peak
        }

        if (nums[0] >= nums[1]) {
            return 0; // The first element is a peak
        }

        if (nums[n - 1] >= nums[n - 2]) {
            return n - 1; // The last element is a peak
        }

        // Iterate through the array to find a peak
        for (int i = 1; i < n - 1; i++) {
            if (nums[i] >= nums[i - 1] && nums[i] >= nums[i + 1]) {
                return i; // Current element is a peak
            }
        }

        return -1; // No peak found
    }

    public static void main(String[] args) {
        int[] nums = {1, 3, 20, 4, 1, 0};

        int peakIndex = findPeakElement(nums);

        if (peakIndex != -1) {
            System.out.println("Peak element: " + nums[peakIndex] + " at index " + peakIndex);
        } else {
            System.out.println("No peak element found");
        }
    }
}
```
## 15. Find the contiguous subarray with the largest sum / Maximum Subarray Sum.
```java
public class MaxSubarraySum {

    public static int maxSubarraySum(int[] nums) {
        int maxEndingHere = nums[0];
        int maxSoFar = nums[0];

        for (int i = 1; i < nums.length; i++) {
            maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }

        return maxSoFar;
    }

    public static void main(String[] args) {
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        int result = maxSubarraySum(nums);
        System.out.println("Maximum Subarray Sum: " + result);
    }
}
```
## 16. Sort an array consisting of only 0s and 1s.
```java
import java.util.Arrays;

public class Main {

    public static void sortBinaryArray(int[] arr) {
        int countZeros = 0;

        // Count the number of zeros
        for (int value : arr) {
            if (value == 0) {
                countZeros++;
            }
        }

        // Fill the array with 
        /* arr: The array to be filled.
            0: The fromIndex, i.e., the index to start filling the array. In this case, it starts from the beginning of the array (arr[0]).
            countZeros: The toIndex, i.e., the index to stop filling the array. It is the count of zeros in the array, so it fills the array up to the last zero.
            0: The value to be stored in each element of the specified range. Here, it is 0, which means filling the specified range with zeros. */
        Arrays.fill(arr, 0, countZeros, 0);

        // Fill the remaining part of the array with ones
        Arrays.fill(arr, countZeros, arr.length, 1);
    }

    public static void main(String[] args) {
        int[] binaryArray = {1, 0, 1, 0, 0, 1, 1, 0, 1};

        System.out.println("Original array: " + Arrays.toString(binaryArray));

        // Sorting the binary array
        sortBinaryArray(binaryArray);

        System.out.println("Sorted array: " + Arrays.toString(binaryArray));
    }
}
```
## 17. Count the number of inversions in an array. An inversion is a pair (i, j) such that i < j and arr[i] > arr[j].
```java
public class InversionCount {

    public static void main(String[] args) {
        int[] array = {1, 20, 6, 4, 5};
        
        System.out.println("Original array:");
        printArray(array);

        long inversionCount = countInversions(array);

        System.out.println("\nNumber of inversions: " + inversionCount);
    }

    static long countInversions(int[] array) {
        // Create a temporary array to store the sorted values during merge
        int[] temp = new int[array.length];
        
        // Start the recursive merge sort and return the inversion count
        return mergeSort(array, temp, 0, array.length - 1);
    }

    static long mergeSort(int[] array, int[] temp, int left, int right) {
        long inversionCount = 0;

        if (left < right) {
            int middle = (left + right) / 2;

            // Recursive calls to count inversions in the left and right halves
            inversionCount += mergeSort(array, temp, left, middle);
            inversionCount += mergeSort(array, temp, middle + 1, right);

            // Merge the two sorted halves and count inversions
            inversionCount += merge(array, temp, left, middle, right);
        }

        return inversionCount;
    }

    static long merge(int[] array, int[] temp, int left, int middle, int right) {
        long inversionCount = 0;

        int i = left;
        int j = middle + 1;
        int k = left;

        // Merge the two sorted halves while counting inversions
        while (i <= middle && j <= right) {
            if (array[i] <= array[j]) {
                temp[k++] = array[i++];
            } else {
                // If array[i] > array[j], it forms inversions with all the remaining elements in the left subarray
                inversionCount += middle - i + 1;
                temp[k++] = array[j++];
            }
        }

        // Copy the remaining elements from the left subarray
        while (i <= middle) {
            temp[k++] = array[i++];
        }

        // Copy the remaining elements from the right subarray
        while (j <= right) {
            temp[k++] = array[j++];
        }

        // Copy the merged elements back to the original array
        for (i = left; i <= right; i++) {
            array[i] = temp[i];
        }

        return inversionCount;
    }

    static void printArray(int[] array) {
        for (int value : array) {
            System.out.print(value + " ");
        }
        System.out.println();
    }
}
```
### 18. Find an equilibrium index in an array, where the sum of elements on its left is equal to the sum of elements on its right.
```java
public class EquilibriumIndex {
    public static int findEquilibriumIndex(int[] arr) {
        int totalSum = 0;
        int leftSum = 0;

        // Calculate the total sum of the array
        for (int num : arr) {
            totalSum += num;
        }

        // Iterate through the array to find the equilibrium index
        for (int i = 0; i < arr.length; i++) {
            totalSum -= arr[i];  // Adjust total sum by subtracting the current element
            if (leftSum == totalSum) {
                return i;  // Found equilibrium index
            }
            leftSum += arr[i];  // Add the current element to the left sum
        }

        // No equilibrium index found
        return -1;
    }

    public static void main(String[] args) {
        int[] array = { -7, 1, 5, 2, -4, 3, 0 };
        int equilibriumIndex = findEquilibriumIndex(array);

        if (equilibriumIndex != -1) {
            System.out.println( "Equilibrium Index: " + equilibriumIndex);
        } else {
            System.out.println("No equilibrium index found.");
        }
    }
}
```

19. **Find Kth Smallest/Largest Element:**
    - Find the Kth smallest or largest element in an array.

20. **Subarray with Given Sum:**
    - Find if there is a subarray with a given sum.

21. **Minimum Jumps to Reach End:**
    - Find the minimum number of jumps needed to reach the end of an array.

23. **Maximum Circular Sum Subarray:**
    - Find the maximum sum subarray in a circular array.

24. **Maximum Length Bitonic Subarray:**
    - Find the length of the maximum length bitonic subarray.

25. **Stock Buy-Sell:**
    - Given stock prices, find the maximum profit that can be obtained by buying and selling.

26. **Two Sum Problem:**
    - Given an array and a target sum, find two numbers in the array that add up to the target.

27. **Pascal's Triangle:**
    - Generate Pascal's Triangle up to a given number of rows.

28. **Find Subarray with 0 Sum:**
    - Determine if there exists a subarray with a sum equal to zero.

29. **Sort an array of 0s, 1s, and 2s:**
    - Sort an array consisting only of 0s, 1s, and 2s without using the built-in sort function.

30. **Find the "Kth" Largest Element:**
    - Find the Kth largest element in an array.

31. **Maximum Length of Consecutive 1s:**
    - Find the maximum length of consecutive 1s in a binary array.

32. **Longest Increasing Subsequence:**
    - Find the length of the longest increasing subsequence of a given array.

33. **Count Triplets with Sum Smaller than a Given Value:**
    - Given an array of distinct integers and a sum value, find the count of triplets with a sum smaller than the given value.

34. **Find the Celebrity:**
    - Given a party of n people, find the celebrity (if any). A celebrity is someone who knows no one but is known by everyone.

35. **Spiral Order Matrix:**
    - Given an m x n matrix, print its elements in spiral order.

36. **Sort an Array of Strings:**
    - Given an array of strings, sort them such that their concatenation results in the lexicographically smallest string.

37. **Find Peak Element in 2D Array:**
    - Find the peak element in a 2D array.

38. **Rain Water Trapping:**
    - Given an array representing heights of bars, calculate the amount of water that can be trapped between the bars.

39. **Find Longest Consecutive Subsequence:**
    - Find the length of the longest consecutive subsequence in an unsorted array.

40. **Find All Duplicates in an Array:**
    - Find all the elements that appear twice in an array.

41. **Sort an Array of 0s, 1s, and 2s (Dutch National Flag Algorithm):**
    - Sort an array consisting only of 0s, 1s, and 2s using the Dutch National Flag algorithm.

42. **Largest Number Formed from an Array:**
    - Given a list of non-negative integers, arrange them to form the largest number.

43. **Minimum Platforms Required:**
    - Given arrival and departure times of trains, find the minimum number of platforms required.

44. **Maximum Sum Rectangle in 2D Matrix:**
    - Find the maximum sum rectangle in a 2D matrix.

45. **Rotate a Matrix:**
    - Given an NxN matrix, rotate it 90 degrees.