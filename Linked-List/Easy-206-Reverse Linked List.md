 [206. Reverse Linked List](https://leetcode-cn.com/problems/reverse-linked-list/) 

Given the head of a singly linked list, reverse the list, and return the reversed list.

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head: 
   return head
        prev = None
        cur = head
        """
        while cur: # need to relink every node
            cur.next, prev, cur = prev, cur, cur.next
        """
        while cur:
            tmp = cur.next
            cur.next = prev
            prev = cur
            cur = tmp

        return prev

```

