## Q230[Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst//) 

### Solution 1 Binary Search
#### Idea:
In-orderly traverse the Trees, In binary search judging target in left or right tree recursively 
#### Time Complexity: 
O(height) (log 2^height)
#### Space Complexity:
O(1)
#### Source code:
```
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
   public int kthSmallest(TreeNode root, int k) {
        int count = countNodes(root.left);
        if(k==count+1){ 
           return root.val;
        }else if (k <= count) {
           return kthSmallest(root.left, k);
        }else  //k > count + 1) 
           return kthSmallest(root.right, k-count-1); 
    }

   public int countNodes(TreeNode n) {
        if (n == null) return 0;
        return 1 + countNodes(n.left) + countNodes(n.right);
    }
}
```
#### Reference:
[Tree Traversal Ways](https://leetcode.com/discuss/43771/implemented-java-binary-search-order-iterative-recursive)
---

