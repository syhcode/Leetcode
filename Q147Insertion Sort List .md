## Q147[Insertion Sort List  ](https://leetcode.com/problems/insertion-sort-list/) 

### Solution 1  
#### Idea:
Use a pointer "pre" to mark the fakehead of sorted list, use a pointer "cur" to mark the element being inserted and use a pointer "next"
to mark the next insert element.Inserting from the head(cur) of the former list to sorted list meanwhile break the former list's head.
#### Time Complexity: 
O(n^2)
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
  public ListNode insertionSortList(ListNode head) {
        if( head == null ){
            return head;
        }

        ListNode helper = new ListNode(Integer.MIN_VALUE); //new starter of the sorted list
        ListNode cur = head;               //the node will be inserted
        ListNode pre = helper;             //insert node between pre and pre.next
        ListNode next = null;             //the next node will be inserted
       
        while( cur != null ){
            next = cur.next;
                //find the right place to insert
            while( pre.next != null && pre.next.val < cur.val ){
                pre = pre.next;
            }
                //insert between pre and pre.next
            cur.next = pre.next;
            pre.next = cur;
            pre = helper;
            cur = next;
        }

        return helper.next;
  }
}
```
#### Reference:

---

