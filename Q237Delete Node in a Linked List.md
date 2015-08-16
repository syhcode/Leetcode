## Q237[Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/) 

### Solution 1 
#### Idea:
Pay attention, node=A can not change original node, it just change the pointer's target position of memory.
Thus this method can not delete when the node is the last node.
#### Time Complexity: 
O(1)
#### Space Complexity:
O(1)
#### Source code:
```
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void deleteNode(ListNode node) {
        node.val=node.next.val;
        node.next=node.next.next;
    }
}
```
#### Reference:
---

