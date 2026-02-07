# leetcode_solved
<details>
<summary><strong>Problem 1: Intersection of Two Arrays 1: </strong></summary>
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.
Example 1:
Input: nums1 = [1,2,2,1], nums2 = [2,2]   Output: [2]  
Example 2:
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]   Output: [9,4]   Explanation: [4,9] is also accepted.

Constraints:
1 <= nums1.length, nums2.length <= 1000    0 <= nums1[i], nums2[i] <= 1000 

Solution:
```python
#Feb 5 2026
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        setA, setB = set(nums1), set(nums2)
        result = list(setA.intersection(setB))
        return result
```
</details>
<details>
<summary><strong>Problem 2: Intersection of two arrays II </strong></summary>
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

Example 1:
Input: nums1 = [1,2,2,1], nums2 = [2,2]     Output: [2,2]  Example 2:
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]  Output: [4,9]   Explanation: [9,4] is also accepted.

Constraints:
1 <= nums1.length, nums2.length <= 1000      0 <= nums1[i], nums2[i] <= 1000
Follow up:
What if the given array is already sorted? How would you optimize your algorithm? What if nums1's size is small compared to nums2's size? Which algorithm is better? What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

Solution:
```python
#Feb 5 2026
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        result1, result2 = {}, {}
        final = []
        for item in nums1:
            result1[item] = result1.get(item, 0) + 1
        for item in nums2:
            result2[item] = result2.get(item, 0) + 1
        for key, value in result1.items():
            if key in result2.keys():
                small = min(result1[key], result2[key])
                for i in range(small):
                    final.append(key)
            else:
                pass
        return final
```
</details>
<details>
<summary><strong>Problem 3: Add Two Numbers - ListNode: </strong></summary>
Example1: Input: l1 = [2,4,3], l2 = [5,6,4]  Output: [7,0,8]  Explanation: 342 + 465 = 807.
Example2: Input: l1 = [0], l2 = [0]   Output: [0]  
Example3: Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]   Output: [8,9,9,9,0,0,0,1]
 
Constraints:  The number of nodes in each linked list is in the range [1, 100].  0 <= Node.val <= 9  It is guaranteed that the list represents a number that does not have leading zeros.
```python
#Feb 6 2026
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        temp1, temp2 = l1, l2
        actual1, actual2 = 0, 0
        n1 = n2 = 1
        while temp1 != None:
            actual1 = actual1 + (temp1.val * n1)
            temp1 = temp1.next
            n1 = n1 * 10
        while temp2 != None:
            actual2 = actual2 + (temp2.val * n2)
            temp2 = temp2.next
            n2 = n2 * 10
        total = actual1 + actual2
        if total == 0:
            return ListNode()
        digit = 0
        head = None
        temp = head
        while total > 0:
            digit = total % 10
            if head == None:
                head = ListNode(digit, None)
                temp = head
            else:
                head.next = ListNode(digit, None)
                head = head.next
            total = total // 10
        return temp
```
</details>
