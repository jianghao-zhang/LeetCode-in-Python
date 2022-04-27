 [61.Rotate list](https://leetcode-cn.com/problems/rotate-list/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        # !0 <= k <= 2 * 10^9!
        # after Nth(N is the length of the Linked List) rotation, the Linked List will become the same as is origin
        if head is None or head.next is None:
            return head

        cur = head
        cnt = 1
        while cur and cur.next:
            cur = cur.next
            cnt += 1
        end = cur

        cur = head
        numRotation = k % cnt
        if numRotation is 0:    # becareful
            return head
        numMove = cnt - numRotation - 1

        for i in range(numMove):
            cur = cur.next

        tmp = cur.next
        cur.next = None
        end.next = head

        return tmp

```

