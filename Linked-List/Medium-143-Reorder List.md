 [143. Reorder List](https://leetcode-cn.com/problems/reorder-list/) 

```Python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reorderList(self, head):
        """
        :type head: ListNode
        :rtype: None Do not return anything, modify head in-place instead.
        """
        middleNode = self.findMiddleNode(head)
        cur1 = head
        tmpHead = middleNode.next
        middleNode.next = None
        cur2 = self.reverseLinkedList(tmpHead)

        while cur2:
            tmp2 = cur2.next
            cur2.next = None
            tmp1 = cur1.next
            cur1.next = cur2
            cur2.next = tmp1

            cur1, cur2 = tmp1, tmp2    


    def findMiddleNode(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        slow = fast = head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next

        return slow
        
    def reverseLinkedList(self, head):
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

