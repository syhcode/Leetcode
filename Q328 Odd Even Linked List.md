## Q328 [Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/) 

### Solution 1 iterative
#### Idea:
mark the two heads of the linked list, consiter the second(even) header in loop moiving two steps each time.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {//1-2-3   
    public ListNode oddEvenList(ListNode head) {
        if(head==null||head.next==null) return head;
        ListNode first=head, second = head.next;
        ListNode first1=head, second2=head.next;
        while(second!=null && second.next!=null){//first =1-3,second =2-null
            first.next=first.next.next;
            first=first.next;
            second.next=second.next.next;
            second=second.next;
        }
        first.next=second2;
        return first1;
    }
}
```
#### Reference:

---

### Solution 2 Divided and Conquer
#### Idea:
insert the first two nodes into finished intermediate linked list. 
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {  
    public ListNode oddEvenList(ListNode head) {
        if(head==null||head.next==null) return head;
        ListNode first= head,second=head.next;
        ListNode p = oddEvenList(head.next.next);
        if(p==null) return head;
        ListNode slow=p;
        ListNode fast=p;
        while(fast!=null && fast.next!=null&&fast.next.next!=null){
            fast=fast.next.next;
            slow=slow.next;
        }
        ListNode temp= slow.next;
        slow.next=second;
        second.next=temp;
        first.next=p;
        return first;
    }
}
```
#### Reference:

---