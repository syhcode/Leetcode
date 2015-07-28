## Q234[Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/) 

### Solution 1 
#### Idea:
Break the list from middle, reverse later part meanwhile appending a rear node of the copy of former part's rear(in case odd length), 
then compare vals  between two parts.
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
    public boolean isPalindrome(ListNode head) {
        if(head==null||head.next==null) return true;
        ListNode slow=head,fast=head;
        while(fast.next!=null&&fast.next.next!=null){
            slow=slow.next;
            fast=fast.next.next;
        }
        // in case of odd or even,add a copy of slow to reversed list.
        ListNode node=reverse(slow.next,slow.val);
        slow.next=null;
        while(head!=null){
            if(head.val==node.val){
                head=head.next;
                node=node.next;
            }
            else return false;
        }
        return true;
    }
    ListNode reverse(ListNode node,int val){
        ListNode pre = new ListNode(val);
        ListNode mark =pre;
        pre.next=node;
        while(node!=null){
            ListNode tmp=node.next;
            node.next=pre;
            pre=node;
            node=tmp;
        }
        mark.next=null;
        return pre;
    }
}
```
#### Reference:

---

