## Q111[ Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/) 

### Solution 1 Recursive
#### Idea:
Use recursive method to deal with each level dividing three cases,which is different from Q104. 
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
    public int minDepth(TreeNode root){
        if(root==null) return 0;
        else if(root.left!=null&&root.right==null)
        return minDepth(root.left)+1;
        else if(root.right!=null&&root.left==null)
        return minDepth(root.right)+1;
        else
        return Math.min(minDepth(root.left),minDepth(root.right))+1;
    }
}

```
#### Reference:

---

