## Q143[ Reorder List ](https://leetcode.com/problems/reorder-list/) 

### Solution 1 
#### Idea:
First in half divide the linked list into two parts,reverse the later half,then merge two lists. 
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
    public void reorderList(ListNode head) {
        ListNode p=head,q=head,tmp1=null,tmp2=null;
        if(head==null||head.next==null||head.next.next==null) return ;
            //divide process
        while(q!=null&&q.next!=null){
            p=p.next;
            q=q.next.next;
        }
        ListNode head1=p.next;
        p.next=null;
            //reverse process
        ListNode mark=head1.next;
        head1.next=null;
        ListNode head2=reverse(head1,mark);
            //merge process
        while(head2!=null){  
            tmp1=head.next;
            tmp2=head2.next;
            head.next=head2;
            head2.next=tmp1;
            head=tmp1;
            head2=tmp2;
        }
    }
    ListNode reverse(ListNode head, ListNode next){
        if(next == null)    return head;
        ListNode temp = next.next;
        next.next = head;
        return reverse(next,temp);

    }
}

```
#### Reference:

---

