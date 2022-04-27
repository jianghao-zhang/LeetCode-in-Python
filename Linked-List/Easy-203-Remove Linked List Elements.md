 [203. Remove Linked List Elements](https://leetcode-cn.com/problems/remove-linked-list-elements/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        prev = ListNode(None) # 在链表头部加上一个节点, 解决掉了第一个就是val的问题
        prev.next = head
        head = prev
        
        # 内部最关键的问题还是两个val连在一起
        while head and head.next: # None的.next 不存在
            if head.next.val is val:
                head.next = head.next.next                
            else: # 当下一个节点的值不是val才移动head到下一个节点，用以解决多个val接连出现的情况
                head = head.next
        
        return prev.next
```

