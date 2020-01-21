---

layout: post

title: Median of Two Sorted Arrays

tags: [data structure]

---

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume **nums1** and **nums2** cannot be both empty.

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        if not nums1 and not nums2:
            return -1
        m, n = len(nums1), len(nums2)
        if (m+n)%2 == 1:
            return self.helper(nums1, nums2, (m+n)//2)
        else:
            return (self.helper(nums1, nums2, (m+n)//2-1) + self.helper(nums1, nums2, (m+n)//2))/2.0
        
    def helper(self, nums1, nums2, k):
        if not nums1:
            return nums2[k]
        if not nums2:
            return nums1[k]
        
        m, n = len(nums1), len(nums2)
        if m//2 + n//2 < k:
            if nums1[m//2] < nums2[n//2]:
                return self.helper(nums1[m//2+1:], nums2, k-m//2-1)
            else:
                return self.helper(nums1, nums2[n//2+1:], k-n//2-1)
        else:
            if nums1[m//2] < nums2[n//2]:
                return self.helper(nums1, nums2[:n//2], k)
            else:
                return self.helper(nums1[:m//2], nums2, k)
```

