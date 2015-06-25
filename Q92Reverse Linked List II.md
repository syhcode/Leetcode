## Q92[Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/) 

### Solution 1
#### Idea:
Reverse as k-group question, and should consider if reverse form head.Also this problem can be solved by build a fake head.
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
    public ListNode reverseBetween(ListNode head, int m, int n) {
        ListNode p=head,q=head,pre=null,mark=null;
        if (head.next==null||m==n) return head;
        while(m>1){
            pre=p;
            p=p.next;
            q=q.next;
            m--;
            n--;
        }
        while(n>1){
            q=q.next;
            n--;
        }   
        mark=q.next;
        reverse(p,q);
        p.next=mark;
        
        // reverse from beginning or not.
        if(pre!=null){
           pre.next=q;
           return head;
        }
        else return q;
    }
    void reverse(ListNode head, ListNode tail){
        if(head==tail) return ;
        reverse(head.next,tail);  //reverse from rear to head.
        head.next.next=head;
    }
}
```
#### Reference:

---

