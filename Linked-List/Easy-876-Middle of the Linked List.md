 [876.Middle of the Linked List](https://leetcode-cn.com/problems/middle-of-the-linked-list/)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def middleNode(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # slow-fast pointer
        slow = head
        fast = head
        
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        
        if fast.next is None:
            return slow
        else:
            return slow.next
```

