 [234. Palindrome Linked List](https://leetcode-cn.com/problems/palindrome-linked-list/)

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):    
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        if head.next is None:
            return True

        # 快慢指针找到链表中间节点，若链表节点个数为奇数个，则将其归入链表前半部分
        # 然后将后半部分的链表反转，逐个比较
        first_half_end = self.end_of_first_half(head)
        second_half_end = self.reverse_list(first_half_end.next)

        # 从两部分链表的头部开始逐个比较
        first_head = head
        second_head = second_half_end
        # 当原始链表节点个数为奇数个时，中间那个节点将不被用于比较
        while first_head and second_head is not None: 
            if first_head.val != second_head.val:
                return False
            else:
                first_head = first_head.next
                second_head = second_head.next

        # 很多情况下我们都不希望原始输入被破坏，所以要将后半段翻转回去
        first_half_end.next = self.reverse_list(second_half_end)

        return True

    def reverse_list(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        prev = None
        while head:
            cur = head
            head = head.next
            cur.next = prev
            prev = cur

        return prev   # be careful

    def end_of_first_half(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        slow = head
        fast = head
        while fast.next is not None and fast.next.next is not None: # 不可接受的是None的.next
            slow = slow.next
            fast = fast.next.next

        return slow
```

