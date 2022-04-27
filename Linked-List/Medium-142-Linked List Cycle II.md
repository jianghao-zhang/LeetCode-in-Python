 [142.Linked List Cycle II](https://leetcode-cn.com/problems/linked-list-cycle-ii/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        slow = fast = head
        while True:
            if not (fast and fast.next): return None
            slow = slow.next
            fast = fast.next.next
            if fast is slow:                 # where encountering, slow node has moved n*b position
                break
        
        fast = head
        while slow is not fast:
            fast = fast.next    # start from head, move a position to the entrance of the cycle 
            slow = slow.next    # if move a+n*b position, the node will come back to the entrance of the cycle

        return slow
      
```

