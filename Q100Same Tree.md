## Q100[Same Tree](https://leetcode.com/problems/same-tree/) 

### Solution 1 Recursive
#### Idea:
In-orderly traverse two Trees, and meanwhile do judgment.
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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p==null&&q==null) return true;
        else if(p!=null&&q!=null){
            if(p.val!=q.val) return false;   
            return isSameTree(p.left,q.left)&&isSameTree(p.right,q.right);
        }
        else return false;
    }
}
```
#### Reference:

---

