## 1. Two Sum
```py
def findMedianSortedArrays(nums1, nums2):
    merged_array = merge_arrays(nums1, nums2)
    length = len(merged_array)

    if length % 2 == 0:
        # If the length is even, return the average of the middle two elements
        mid1 = length // 2
        mid2 = mid1 - 1
        return (merged_array[mid1] + merged_array[mid2]) / 2.0
    else:
        # If the length is odd, return the middle element
        mid = length // 2
        return merged_array[mid]

def merge_arrays(nums1, nums2):
    merged_array = []
    i = j = 0

    while i < len(nums1) and j < len(nums2):
        if nums1[i] < nums2[j]:
            merged_array.append(nums1[i])
            i += 1
        else:
            merged_array.append(nums2[j])
            j += 1

    merged_array.extend(nums1[i:])
    merged_array.extend(nums2[j:])

    return merged_array

# Example usage
nums1 = [1, 3]
nums2 = [2]
median = findMedianSortedArrays(nums1, nums2)
print("Median:", median)
```