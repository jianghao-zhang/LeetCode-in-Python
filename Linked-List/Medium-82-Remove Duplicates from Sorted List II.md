 [82. Remove Duplicates from Sorted List II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # in 83 Remove Duplicates from Sorted List, duplicate numbers will still appear once
        # be careful of the case "[]", "[x]"
        if head is None or head.next is None:
            return head
        
        dummyNode = ListNode(None)
        dummyNode.next = head
        cur = dummyNode
        tmp = None

        while cur.next:
            # be careful of the case"[x, x]", so put the condition "cur.next.val==tmp" on the first
            if cur.next.next:
                if cur.next.val == tmp or cur.next.next.val == cur.next.val: 
                    tmp = cur.next.val
                    cur.next = cur.next.next
                else: 
                    tmp = None
                    cur = cur.next
            else:
                if cur.next.val == tmp:
                    cur.next = cur.next.next
                else:
                    cur = cur.next

        return dummyNode.next

```

