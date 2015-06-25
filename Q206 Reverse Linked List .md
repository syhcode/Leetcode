## Q206[ Reverse Linked List ](https://leetcode.com/problems/reverse-linked-list/) 

### Solution 1 Recursive
#### Idea:
First make head.next=null, then can process the remained by let the next.next=head after marking next.next.
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
 *     ListNode(int x) { val = x; }
 * }
 */
 
public class Solution {
    public ListNode reverseList(ListNode head) {
        if(head == null) return head;
        ListNode next = head.next;
        head.next = null;

        return recursive(head,next);
    }

    private ListNode recursive(ListNode head, ListNode next){
        if(next == null)    return head;
        ListNode temp = next.next;
        next.next = head;
        return recursive(next,temp);

    }
}

```
#### Reference:

---

