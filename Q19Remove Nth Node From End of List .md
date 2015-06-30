## Q19[ Remove Nth Node From End of List  ](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) 

### Solution 1 Two Pointers
#### Idea:
Let gap between two pointers is n, and move two pointers to the end of linked list.
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
   public ListNode removeNthFromEnd(ListNode head, int n){

    ListNode fake = new ListNode(0);
    ListNode slow = fake, fast = fake;
    fake.next = head;

    //make gap between slow and fast into n
    for(int i=0; i<=n; i++){
        fast = fast.next;
    }
    while(fast != null) {
        slow = slow.next;
        fast = fast.next;
    }
    slow.next = slow.next.next;
    return fake.next;
    }
}
```
#### Reference:

---

