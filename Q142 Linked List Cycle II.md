## Q142[ Linked List Cycle II ](https://leetcode.com/problems/linked-list-cycle-ii/) 

### Solution 1 Two Pointers
#### Idea:
Use a fast moving and a slow moving pointer,if they run in a circle they must meet.	And if there is a distance(k steps) between head and merge node thus "fast" move in cycle k steps earlier than "slow",
since "fast" move one more step each time than "slow",then the meet point should be earlier k steps to merge node.Thus can find merge node depending on meet node and head. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
 
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast!=null && fast.next!=null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) break;
        }
        if (fast==null || fast.next==null) return null;
        while (head!= fast) {
            head = head.next;
            fast = fast.next;
        }
        return fast;
    }
}
```

#### Reference:

---

