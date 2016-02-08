## Q98[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

### Solution 1 Recursive
#### Idea:
BST: all left children nodes is smaller than its parent Node,all right children nodes is greater than its parent Node,judging recursively.
is smaller than Integer.MIN_VALUE. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isValidBST(TreeNode root) {
       return helper(root, Long.MIN_VALUE,Long.MAX_VALUE);
    }
    public boolean helper(TreeNode root, long minval, long maxval){
        if(root==null) return true;
        return root.val>minval&&root.val<maxval&&helper(root.left,minval,root.val)&&helper(root.right,root.val,maxval);
    }
}
```
### Solution 2 iterative,stack
#### Idea:
use Stack for inorder traversal,mark the pre-visited root and compare.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean isValidBST(TreeNode root) {
        if(root == null) return true; 
        Stack<TreeNode> sk = new Stack<TreeNode>();
        sk.push(root);
        TreeNode pre =null;
        while(!sk.isEmpty()){
            while(root.left!=null){
                root=root.left;
                sk.push(root);
            } 
            TreeNode temp=sk.pop();
            if(pre!= null && pre.val>=temp.val ) return false;
            pre=temp;
            if(temp.right!=null){
                root=temp.right;
                sk.push(root);
            }
        }
        return true;
    }
}
```
#### Reference:
```
 Integer.MIN_VALUE = -2147483648
 Integer.MAX_VALUE = 2147483647
 Long.MIN_VALUE = -9223372036854775808
 Long.MAX_VALUE = 9223372036854775807
 Float.MIN_VALUE = 1.4E-45
 Float.MIN_NORMAL = 1.17549435E-38
 Float.MAX_VALUE = 3.4028235E38
 Double.MAX_VALUE = 1.7976931348623157E308
 Double.MIN_VALUE = 4.9E-324
```

