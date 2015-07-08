## Q222[ Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/) 

### Solution 1 Recursive
#### Idea:
Find the depth  of left and right children of the complete binary tree, 
if depth left>right,then left is complete tree and right is full tree(level-1),
if depth left=right,then left is full tree and right is complete tree, and casing these two situations count nodes half by half recursively. 
#### Time Complexity: 
O(log(n)^2)
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
    public int countNodes(TreeNode root){
        int count = 0;
        if(root==null) return 0;
        int LeftHalfLevel = getLevel(root.left);
        int RightHalfLevel = getLevel(root.right);
        if(LeftHalfLevel>RightHalfLevel){
            count = (1<<RightHalfLevel) + countNodes(root.left);
        }else{
            count = (1<<LeftHalfLevel) + countNodes(root.right);
        }
        return count;
    }
    public static int getLevel(TreeNode root){
        if(root==null) return 0;
        int level = 0;
        while(root!=null){
            level++;
            root=root.left;
        }
    return level;
    }

}

```
#### Reference:

---

