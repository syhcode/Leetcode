## Q98[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

### Solution 1 Recursive
#### Idea:
Same as Q99, depend on in-order traversal sequence to do judgment.Pay a attention to the initiation of "pre" when the input "val"
is smaller than Integer.MIN_VALUE. 
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
    boolean l=true;
    boolean firstTime=true;
    
    //can not initiate with MIN_VALUE for Long or Integer.
    TreeNode pre = new TreeNode(0); 
    
    public boolean isValidBST(TreeNode root) {
        if(root==null) return true;
        if(root.left==null&&root.right==null) return true;
        judge(root);
        return l;
        
    }
    void judge(TreeNode root){
        if (root==null) return;
        judge(root.left);
        if (!firstTime&&pre.val >= root.val) l=false;
        pre=root;
        firstTime=false;
        judge(root.right);

    }
}
```
#### Reference:

---

