## Q148[ Sort List  ](https://leetcode.com/problems/sort-list/) 

### Solution 1 Merge Sort,Recursive
#### Idea:
Divide the list and use merge sort method recursively.
#### Time Complexity: 
O(nlog(n))
#### Space Complexity:
O(log(n))
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
    public ListNode sortList(ListNode head) {
        if (head == null || head.next == null)
            return head;
        ListNode fast = head.next.next;
        ListNode slow = head;
        
        //get the middle pointer
        while (fast != null && fast.next != null) {
            slow =slow.next;
            fast =  fast.next.next;
        }
        
        ListNode h2 = sortList(slow.next);
        slow.next = null;
        ListNode h1=sortList(head);
        return merge(h1, h2);
    }
    public ListNode merge(ListNode h1, ListNode h2) {
        ListNode fake = new ListNode(0);
        ListNode p=fake;
        while (h1 != null && h2 != null) {
            if (h1.val < h2.val) {
                p.next = h1;
                h1 = h1.next;
            }
            else {
                p.next = h2;
                h2 = h2.next;
            }
            p = p.next;
        }
        if (h1 != null)
            p.next = h1;
        if (h2 != null)
            p.next = h2;
        return fake.next;

    }
}
```
#### Reference:

---

