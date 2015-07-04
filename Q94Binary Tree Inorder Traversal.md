## Q94[ Binary Tree Inorder Traversal ](https://leetcode.com/problems/binary-tree-inorder-traversal/) 

### Solution 1 stack
#### Idea:
First put all left children in stack,then right's left.And in proper traversal timing store elements in res.
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
    public List<Integer> inorderTraversal(TreeNode root) {
        Stack<TreeNode> s=new Stack<>();
        List<Integer> res=new ArrayList<>();
        if(root==null) return res;
        s.push(root);
        while(s.peek().left!=null){
            TreeNode tmp=s.peek();
            s.push(tmp.left);
        }
        while(!s.isEmpty()){
            TreeNode tmp1=s.pop();
            res.add(tmp1.val);
            if(tmp1.right!=null){
                s.push(tmp1.right);
                while(!s.isEmpty()&&s.peek().left!=null){
                TreeNode tmp2=s.peek();
                s.push(tmp2.left);
                }
            }
             
        }
        return res;
    }
}
```
#### Reference:

---

