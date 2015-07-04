## Q145[ Binary Tree Postorder Traversal ](https://leetcode.com/problems/binary-tree-postorder-traversal/) 

### Solution 1 Recursive
#### Idea:
In each recursive traversal level, process this level and save this level's val in res.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
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
    public List<Integer> postorderTraversal(TreeNode root) {
        Stack<TreeNode> s=new Stack<>();
        List<Integer> res=new ArrayList<>();
        if(root==null) return res;
        postrun(root,res);
        return res;
    }
    void postrun(TreeNode root,List<Integer> res){
         if(root.left!=null) postrun(root.left,res);
         if(root.right!=null) postrun(root.right,res);
         res.add(root.val);
        
    }
}
```
#### Reference:

---

