 [237.Delete Node in a Linked List](https://leetcode-cn.com/problems/delete-node-in-a-linked-list/) 

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        # since we can not gain the prev link
        # the method is "preserve the current node" and "delete the next node"

        node.val = node.next.val
        node.next = node.next.next

```

