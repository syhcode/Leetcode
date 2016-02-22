## Q21[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) 

### Solution 1
#### Idea:
Link two lists' elements in order considering different length cases.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) { 
        ListNode dummy = new ListNode(0);
        ListNode pre = dummy;
        while(l1!=null && l2!=null){
            if(l1.val<l2.val) {
                pre.next=l1;
                l1=l1.next;
            }else{
                pre.next=l2;
                l2=l2.next;
            }
            pre=pre.next;
        }
        pre.next=l1!=null?l1:l2;
        return dummy.next;
    }
}
```
#### Reference:

---

