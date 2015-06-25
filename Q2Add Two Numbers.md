## Q2[Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) 

### Solution 1
#### Idea:
Consider cases:two lists add digit by digit; one list add carry in remained digit; result add final carry.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2)
    {
        ListNode head = new ListNode(0); 
        ListNode l3 = head;
        int sum = 0;
        // If both are not done 
        while (l1 != null && l2 != null)
        {
            sum /= 10;
            sum += l1.val + l2.val;
            l1 = l1.next;
            l2 = l2.next;
            l3.next = new ListNode(sum % 10);
            l3 = l3.next;
        }
        // If one of them is not done 
        if (l1 != null || l2 != null)
        {
           
            ListNode l = (l1 != null) ? l1 : l2;
            while (l != null)
            {
                sum /= 10;
                sum += l.val;
                l3.next = new ListNode(sum % 10);
                l3 = l3.next;
                l = l.next;
            }
        }
        //judge the final carry situation.
        if (sum / 10 == 1) l3.next = new ListNode(1);
        return head.next;
    }
}
```
#### Reference:

---

