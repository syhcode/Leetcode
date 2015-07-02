## Q109[Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/) 

### Solution 1 Recursive
#### Idea:
Same as Q148 merge sort recursive method.
In order to build a BST, just recursively let left-half sorted list elements to left child tree and let right-half sorted list elements to right child tree. 
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
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
 
public class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        if (head ==null)
            return null;
        if (head.next == null)
            return new TreeNode(head.val);
        ListNode fast = head.next.next,slow = head;
        while (fast != null&& fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        TreeNode root = new TreeNode(slow.next.val);
        root.right = sortedListToBST(slow.next.next);
        slow.next = null;
        root.left = sortedListToBST(head);
        return root;
    }
}
```
#### Reference:

---

