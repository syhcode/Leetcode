## Q141[ Linked List Cycle ](https://leetcode.com/problems/linked-list-cycle/) 

### Solution 1 Two Pointers
#### Idea:
Use a fast moving and a slow moving pointer,if they run in a circle they must meet. 
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
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while(fast != null && fast.next != null)
        {
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast)
                return true;
        }
        return false;
    }
}
```
### Solution 2 
#### Idea:
Break the list. Let each element point at itself( a mark method) after break processing, if find a element point at itself(be marked),
then it must be point by the former element.
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
    public boolean hasCycle(ListNode head) {
      ListNode tmp;
      while(head!=null){
        if(head.next == head) return true;
        tmp=head.next;
        head.next=head;
        head=tmp;
      }
       return false;

   }
}
```
#### Reference:
[does-everyone-solved-it-with-o-n-complexity](https://leetcode.com/discuss/122/does-everyone-solved-it-with-o-n-complexity)
---

