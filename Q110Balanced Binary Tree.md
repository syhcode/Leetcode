## Q110[ Balanced Binary Tree ](https://leetcode.com/problems/balanced-binary-tree/) 

### Solution 1 Recursive
#### Idea:
From the end level count the depth of each level of the tree recursively,and judge depending on these depth.
#### Time Complexity: 
O(n)
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
    private boolean result=true;
    public boolean isBalanced(TreeNode root) {
        maxDepth(root);
        return result;
    }

    public int maxDepth(TreeNode root) {
        if (root == null)
            return 1;
        int l = maxDepth(root.left);
        int r = maxDepth(root.right);
        if (Math.abs(l - r) > 1)
        result = false;
        return 1+Math.max(l, r);
    }
}
```
#### Reference:

---

