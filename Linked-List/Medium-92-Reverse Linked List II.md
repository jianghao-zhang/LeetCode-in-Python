 [92. Reverse Linked List II](https://leetcode-cn.com/problems/reverse-linked-list-ii/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseBetween(self, head, left, right):
        """
        :type head: ListNode
        :type left: int
        :type right: int
        :rtype: ListNode
        """
        if head.next is None:
            return head

        dummyNode = ListNode(None)
        dummyNode.next = head
        tmp = dummyNode
        
        for i in range(left-1):
            tmp = tmp.next
        tailLeft = tmp
        tmp = tmp.next
        targetHead = tailLeft.next
        tailLeft.next = None
        
        for i in range(right-left):
            tmp = tmp.next
        headRight = tmp.next
        tmp.next = None

        rhead = self.reverseList(targetHead)
        tailLeft.next = rhead
        while rhead and rhead.next:
            rhead = rhead.next
        rhead.next = headRight

        return dummyNode.next


    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        pre = None
        cur = head

        while cur:
            tmp = cur.next
            cur.next = pre
            pre = cur
            cur = tmp

        return pre
```

