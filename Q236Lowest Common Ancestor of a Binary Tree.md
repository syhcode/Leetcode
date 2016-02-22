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
public class Solution { // assume p,q must under the root.
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {//if only one target node in this tree, return this node.
     if (root == null || root== p || root==q ) return root;
        TreeNode left=lowestCommonAncestor(root.left, p, q); 
        TreeNode right=lowestCommonAncestor(root.right, p, q);
        if (left==p && right==q || left==q && right==p ) return root; // p become root not found q Or q is root not found p.
        else return left==null? right:left;  // be p or q
    }
} 
```
#### Reference:
---

