## Q101[Symmetric Tree](https://leetcode.com/problems/symmetric-tree/) 

### Solution 1 Recursive
#### Idea:
Like Q100 idea, in-orderly and in-symmetric-orderly traverse two sub-trees respectively, and meanwhile do judgment.
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
    public boolean isSymmetric(TreeNode root) {
        if(root==null||root.left==null&&root.right==null) return true;
        else if(root.left!=null&&root.right!=null)
        return judge(root.left,root.right);
        else return false;
    }
    boolean judge(TreeNode p,TreeNode q){
        if(p==null&&q==null) return true;
        else if(p!=null&&q!=null){
            if(p.val!=q.val) return false;   
            return judge(p.left,q.right)&&judge(p.right,q.left);
        }
        else return false;
    }
}
```
#### Reference:

---

