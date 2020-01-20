Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.<br>

Example:<br>

Input: 1->2->4, 1->3->4 <br>
Output: 1->1->2->3->4->4 <br>

<br>
Solution:<br>

<!-- # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
 -->

class Solution:<br>
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:<br>
        
        if not l1 or not l2:
            return l1 or l2
        if l1.val < l2.val:
            l1.next = self.mergeTwoLists(l1.next, l2)
            return l1
        else:
            l2.next = self.mergeTwoLists(l1, l2.next)
            return l2
        
class Solution2:<br>
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:<br>
        
        head = tail = ListNode(0)
        while l1 and l2:
            if l1.val < l2.val:
                tail.next = l1
                l1 = l1.next
            else:
                tail.next = l2
                l2 = l2.next
            tail = tail.next
        tail.next = l1 or l2
        return head.next