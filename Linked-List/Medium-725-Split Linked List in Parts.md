#### [725. Split Linked List in Parts](https://leetcode-cn.com/problems/split-linked-list-in-parts/)

```python
# Definition for singly-linked list.
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def splitListToParts(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: List[ListNode]
        """
        ls = []
        length = self.getLength(head)
        splitSeq = self.splitSequence(length, k)
        cur = head
        for i in range(k):
            tmpHead = cur
            if splitSeq[i]-1 > 0:
                for i in range(splitSeq[i]-1):
                    cur = cur.next
                nextHead = cur.next
                cur.next = None
                ls.append(tmpHead)
                cur = nextHead
            elif splitSeq[i]-1 == 0:
                nextHead = cur.next
                cur.next = None
                ls.append(tmpHead)
                cur = nextHead
            elif splitSeq[i]-1 < 0:
                ls.append(None)
        return ls


    def splitSequence(self, length, k):
        """
        :type length: number of nodes in the given linked list, int
        :type k: number of parts the given linked list should be splited, int
        return splitSeq: List[int]
        """
        splitSeq = []

        if k >= length:
            for i in range(length):
                splitSeq.append(1)
            for i in range(k-length):
                splitSeq.append(0)
        elif k < length:
            # x* (minPart+1) + (k-x)* minPart = length
            # x*minPart + x + k*minPart -x*minPart
            # k*minPart + x = length
            minPart = int(length//k)
            x = length - k*minPart
            for i in range(x):
                splitSeq.append(minPart+1)
            for i in range(k-x):
                splitSeq.append(minPart)
            
        return splitSeq
            

    def getLength(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head:
            return 0
        
        cur, cnt = head, 0
        while cur:
            cnt += 1
            cur = cur.next
        return cnt

```

