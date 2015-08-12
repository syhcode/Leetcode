## Q236[Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) 

### Solution 1 Recursive
#### Idea:
Find p or q recursively to judge the ancestor node, instead of its value .
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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
         if(root==null||root==p||root==q) return root;  //compare Object,not .val
         TreeNode left= lowestCommonAncestor(root.left,p,q);
         TreeNode right= lowestCommonAncestor(root.right,p,q);
         if(left!=null&&right!=null) return root;
         else return left==null?right:left;
    }
}
```
#### Reference:
---

