 [19. Remove Nth Node From End of List ](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        dummyNode = ListNode(None)
        dummyNode.next = head

        if dummyNode.next.next is None:
            return None

        slow = fast = dummyNode
        cur = dummyNode
        cnt = 0
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
            cnt += 1

        if fast.next is not None:
            nodeNum = (cnt+1)*2
        else:
            nodeNum = (cnt+1)*2-1
        
        for i in range(nodeNum-n-1):
            cur = cur.next
        
        cur.next = cur.next.next

        return dummyNode.next
        
```

