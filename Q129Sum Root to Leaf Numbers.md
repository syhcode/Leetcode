## Q129[Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/) 

### Solution 1 Backtracking
#### Idea:
DFS and backtrack. When reach the leaf update the sum.
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
    int sum=0;
    int cur=0;
    public int sumNumbers(TreeNode root) {
        getSum(root);
        return sum;
    }
    void getSum(TreeNode root){
        int pre=cur;
        if(root==null)return;
        if(root.left==null&&root.right==null){
           cur=cur*10+root.val;
           sum=cur+sum;
        }
        else cur=cur*10+root.val;
        getSum(root.left);
        getSum(root.right);
        
        cur=pre; //backtrack
    }
}
```
#### Reference:

---

