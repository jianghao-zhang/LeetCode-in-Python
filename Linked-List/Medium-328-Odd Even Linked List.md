 [328. Odd Even Linked List](https://leetcode-cn.com/problems/odd-even-linked-list/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def oddEvenList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # better solution: use odd and even pointers method
        if not (head and head.next):
            return head
        
        odd, even, evenHead = head, head.next, head.next
        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = evenHead
        
        return head

        '''
        if not (head and head.next):
            return head

        dummyNode = ListNode(None)
        dummyNode.next = head
        
        cur, queue = dummyNode, []
        while cur.next and cur.next.next:
            queue.insert(0, cur.next.next)
            cur.next.next = cur.next.next.next
            cur = cur.next
            queue[0].next = None              # need to remove all the next connection of even nodes
        if cur.next is not None:              # [x,x,x,x,x]
            cur = cur.next

        while len(queue) is not 0:
            cur.next = queue.pop()
            cur = cur.next
        
        return dummyNode.next
        '''
```

