## Q86[Partition List ](https://leetcode.com/problems/partition-list/) 

### Solution 1 
#### Idea:
Build two lists, one to save node.val<x, another to save the rest,and finally link two lists.
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
  public ListNode partition(ListNode head, int x) {
    ListNode node1 = new ListNode(0), node2 = new ListNode(0); 
    ListNode cur1 = node1, cur2 = node2; 
    while (head!=null){
        if (head.val<x) {
            cur1.next = head;
            cur1 = cur1.next;
        }else {
            cur2.next = head;
            cur2 = cur2.next;
        }
        head = head.next;
    }
    cur2.next = null; //process real,avoid cycle in linked list.
    cur1.next = node2.next;
    return node1.next;
  }
}
```

#### Reference:

---

