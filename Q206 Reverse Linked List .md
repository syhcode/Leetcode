## Q206[ Reverse Linked List ](https://leetcode.com/problems/reverse-linked-list/) 

### Solution 1 Recursive
#### Idea:
First make head.next=null, then can process the remained by let the next.next=head after marking next.next.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre =null;
        return helper(pre, head);
    }
    ListNode helper(ListNode pre,ListNode head){
        if(head == null) return pre;
        ListNode temp = head.next;
        head.next=pre;
        return helper(head,temp);
    }
}

```
### Solution 2 Iterative
#### Idea:
use pre and temp nodes to record.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode temp = null;
        while(head!=null){
            temp=head.next;
            head.next=pre;
            pre=head;
            head=temp;
        }
        return pre;
    }
}
```
#### Reference:

---

