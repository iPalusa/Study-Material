## 1. Two Sum
```java
import java.util.HashMap;

public class TwoSum {

    public static int[] twoSum(int[] nums, int target) {
        // Create a HashMap to store the elements and their indices
        HashMap<Integer, Integer> map = new HashMap<>();

        // Iterate through the array
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            // Check if the complement is already in the map
            if (map.containsKey(complement)) {
                // Return the indices of the two numbers
                return new int[]{map.get(complement), i};
            }

            // Put the current element and its index into the map
            map.put(nums[i], i);
        }

        // If no solution is found, return an empty array
        return new int[0];
    }

    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;

        int[] result = twoSum(nums, target);

        System.out.println("Output: [" + result[0] + ", " + result[1] + "]");
    }
}
```
## 2. Median of Two Sorted Arrays
```java
public class MedianOfTwoSortedArrays {

    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int[] mergedArray = mergeArrays(nums1, nums2);

        int length = mergedArray.length;

        if (length % 2 == 0) {
            // If the length is even, return the average of the middle two elements
            int mid1 = length / 2;
            int mid2 = mid1 - 1;
            return (mergedArray[mid1] + mergedArray[mid2]) / 2.0;
        } else {
            // If the length is odd, return the middle element
            int mid = length / 2;
            return mergedArray[mid];
        }
    }

    private static int[] mergeArrays(int[] nums1, int[] nums2) {
        int[] mergedArray = new int[nums1.length + nums2.length];

        int i = 0, j = 0, k = 0;

        while (i < nums1.length && j < nums2.length) {
            if (nums1[i] < nums2[j]) {
                mergedArray[k++] = nums1[i++];
            } else {
                mergedArray[k++] = nums2[j++];
            }
        }

        while (i < nums1.length) {
            mergedArray[k++] = nums1[i++];
        }

        while (j < nums2.length) {
            mergedArray[k++] = nums2[j++];
        }

        return mergedArray;
    }

    public static void main(String[] args) {
        int[] nums1 = {1, 3};
        int[] nums2 = {2};
        double median = findMedianSortedArrays(nums1, nums2);
        System.out.println("Median: " + median);
    }
}
```
## 3. Container with Most Water

![](Container%20with%20most%20water.jpg)
```java
public class ContainerWithMostWater {
    public int maxArea(int[] height) {
        int maxArea = 0;
        int left = 0;
        int right = height.length - 1;

        while (left < right) {
            // Calculate the width and height of the container
            int width = right - left;
            int minHeight = Math.min(height[left], height[right]);

            // Update the maximum area if the current area is greater
            maxArea = Math.max(maxArea, width * minHeight);

            // Move the pointers towards the center
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }

    // Example usage:
    public static void main(String[] args) {
        ContainerWithMostWater containerWithMostWater = new ContainerWithMostWater();

        // Example input: [1,8,6,2,5,4,8,3,7]
        int[] height = {1, 8, 6, 2, 5, 4, 8, 3, 7};

        // Call the maxArea function
        int result = containerWithMostWater.maxArea(height);

        // Print the result
        System.out.println("Maximum area of the container: " + result);
    }
}
```