## Q24[Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) 

### Solution 1 Recursive
#### Idea:
Since swap should begin in end of node,use recursive method dealing swapping and linking to next head.
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
    public ListNode swapPairs(ListNode head) {
        if ((head == null)||(head.next == null))
            return head;
        ListNode n = head.next;
        head.next = swapPairs(head.next.next);
        n.next = head;
        return n;
    }
}

***Or use two parameters function:

public class Solution {
  
    public ListNode swapPairs(ListNode head) {
        ListNode node=head;
        if(node==null||node.next==null) return node;
        ListNode res=reverse(node,node.next);
        return res;
    }
    ListNode reverse(ListNode node,ListNode next){
        if(node==null||next==null) return node;
        else if(next.next==null){
            node.next.next=node;
            node.next=null;
            return next;
        }
        else{
        ListNode tail=reverse(next.next,next.next.next);
        ListNode tmp=next;
        node.next.next=node;
        node.next=tail;
        return next;
        }
    }
  
}
```

#### Reference:

---

