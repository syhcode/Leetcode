## Q25[Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) 

### Solution 1Recursive
#### Idea:
Use recursive method to deal every k-section of the list , and for each section reverse the linked element recursively.
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
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode p=head,mark=head,pre=null;
        int i=0;
        
       // judge the k section
       while(i<k&&p!=null){
            pre=p;
            p=p.next;
            i++;
        }
        if(i<k)   return head;
        p=pre;            // get the rear position (p) of k section.
        head=p.next;      //update next head of potential k section.
        reverse(mark,p);  //reverse k section, p move from rear to head.
        mark.next=reverseKGroup(head,k);  //now head become rear and link next 'p'.
        return p;         //now p is head of the k section.
        
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

