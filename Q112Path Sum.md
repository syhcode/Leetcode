## Q112[Path Sum](https://leetcode.com/problems/path-sum/) 

### Solution 1 Recursive
#### Idea:
Use recursive method to deal with each level.
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
    public boolean hasPathSum(TreeNode root, int sum) {
        if(root==null) return false;
        if(root.left==null&&root.right==null&&sum==root.val) return true;
        return hasPathSum(root.left,sum-root.val)||hasPathSum(root.right,sum-root.val);

    }
}

```
#### Reference:

---

