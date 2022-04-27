 [138. Copy List with Random Pointer](https://leetcode-cn.com/problems/copy-list-with-random-pointer/) 

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x, next=None, random=None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: Node
        :rtype: Node
        """
        # the main problem is how to constrcut the random connections the same as the original list
        # use the hash map/dictionary to indicate the random connection!
        if head is None:
            return None
        
        d = dict()
        cur = head
        while cur:
            d[cur] = Node(cur.val)
            cur = cur.next
        
        cur = head
        while cur:
            if cur.next:   # build the "next" connection
                d[cur].next = d[cur.next]
            if cur.random:    # build the "random" connection
                d[cur].random = d[cur.random]
            cur = cur.next

        return d[head]

```

