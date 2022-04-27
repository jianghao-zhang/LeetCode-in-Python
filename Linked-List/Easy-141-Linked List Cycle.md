#### [141. Linked List Cycle](https://leetcode-cn.com/problems/linked-list-cycle/)

 Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

---

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """

        # we can use two pointers: "fast" and "slow"
        # the "fast" pointer moves two steps per time, while the "slow" one moves one step only per time
        # if there is a loop within the linked list, the faster one will always jump into the loop firstly
        # cuz the fast one moves one step faster than the slow one, so the situation is just like the faster one is chasing the slower 
        # one with the speed of one step

        if not head: return False
        slow, fast = head, head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if fast == slow:
                return True
        return False

```



