## Q160[Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/) 

### Solution 1
#### Idea:
Since a intersection exists inside both linked lists and then two lists merge together,thus move lists' head to the same start point.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
 
 
public class Solution {
  public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    int lenA = length(headA), lenB = length(headB);
    // move headA and headB to the same start point
    while (lenA > lenB) {
        headA = headA.next;
        lenA--;
    }
    while (lenA < lenB) {
        headB = headB.next;
        lenB--;
    }
    // search the intersection until end
    while (headA != headB) {
        headA = headA.next;
        headB = headB.next;
    }
     return headA;
  }

    private int length(ListNode node) {
        int length = 0;
         while (node != null) {
        node = node.next;
        length++;
         }
         return length;
    }
}
```
#### Reference:

---

