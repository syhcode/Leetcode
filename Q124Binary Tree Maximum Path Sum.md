## Q124[ Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) 

### Solution 1 Recursive
#### Idea:
Use recursive method to deal with each level:get the maxvalue of path through the sub-root of this level(left-half+right-half recursively),
and update maxvalue by comparing with the former maxvalue.
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
    private int maxValue=Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        maxRoot(root);
        return maxValue;
    }

    private int maxRoot(TreeNode node) {
        if (node == null) return 0;
        //considering negative number,divide sum into left and right process.
        int left = Math.max(0, maxRoot(node.left));
        int right = Math.max(0, maxRoot(node.right));
        maxValue = Math.max(maxValue, left + right + node.val);
        
        return Math.max(left, right) + node.val;
    }
}


```
#### Reference:

---

