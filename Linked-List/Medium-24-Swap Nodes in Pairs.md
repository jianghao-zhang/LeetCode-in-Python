 [24. Swap Nodes in Pairs](https://leetcode-cn.com/problems/swap-nodes-in-pairs/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next:
            return head

        dummyNode = ListNode(None)
        dummyNode.next = head
        
        stack = []
        cur = dummyNode
        while cur.next and cur.next.next:
            stack.append(cur.next)
            stack.append(cur.next.next)
            tmp = cur.next.next.next
            cur.next = stack.pop()
            cur.next.next = stack.pop()
            cur = cur.next.next
            cur.next = tmp

        return dummyNode.next

```

