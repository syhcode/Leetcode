## Q82[Remove Duplicates from Sorted List II ](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/) 

### Solution 1 Two List Pointers
#### Idea: 
Build a FakeHead to deal with the edge problems.
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
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null) return null;
        ListNode FakeHead=new ListNode(0);
        FakeHead.next=head;
        ListNode res=FakeHead;
        ListNode cur=head;
        while(cur!=null){      //each time cur should has a different val,res modify the list.
            while(cur.next!=null&&cur.val==cur.next.val){
                cur=cur.next;
            }
            if(res.next!=cur){  //exist duplicates,skip to cur.next
               res.next=cur.next;
            }
            else{             //to now no duplicates,skip next step. 
               res=res.next;
            }
            cur=cur.next;
        }
        return FakeHead.next;
    }
}
```
## Q83[Remove Duplicates from Sorted List I ](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

### Solution 1 Two List Pointers
#### Idea: 
A simplified question of Q82.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
 
public class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode list=head;
        while(list!=null){
            while(list.next!=null&&list.val==list.next.val){
                list.next=list.next.next;
            }
            list=list.next;
        }
        return head;
    }
}
#### Reference:

---

