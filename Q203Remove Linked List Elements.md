## Q203[Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/) 

### Solution 1
#### Idea:
Remove the beginning target elements meanwhile update head,then remove the target elements in linked list.
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
    public ListNode removeElements(ListNode head, int val) {
        ListNode list=head;
        if(list==null) return list;
        while(list!=null&&list.val==val){
            list=list.next;
        }
        head=list;
        while(list!=null){
           while(list.next!=null&&list.next.val==val) //considering continuing target elements.
            list.next=list.next.next;
            list=list.next;
        }
        
        return head;
    }
}
```
#### Reference:

---

