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
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1==null&&l2==null) return null;
        if(l1==null) return l2;
        if(l2==null) return l1;
        ListNode res=new ListNode(0);
        ListNode list=res;
        while(l1!=null&&l2!=null){
            if(l1.val<=l2.val){
            list.next=l1;
            l1=l1.next;    
            }
            else{
                list.next=l2;
                l2=l2.next;
            }
            list=list.next;
        }
        
        if(l1!=null) list.next=l1;
        if(l2!=null) list.next=l2;
            
        return res.next;
    }
}
```
#### Reference:

---

