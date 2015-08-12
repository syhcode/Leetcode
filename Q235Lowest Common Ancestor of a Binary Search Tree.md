## Q235[Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) 

### Solution 1 Recursive
#### Idea:
Cases analysis .
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
         if(root.val==p.val) return p;
         else if(root.val==q.val) return q;
         else if(root.val>p.val&&root.val>q.val&&root.left!=null)
             return lowestCommonAncestor(root.left,p,q);
         else if(root.val<p.val&&root.val<q.val&&root.right!=null)
             return lowestCommonAncestor(root.right,p,q);
         else return root;
    }
}
```
#### Reference:
---

