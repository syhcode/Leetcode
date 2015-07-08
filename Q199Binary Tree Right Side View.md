## Q199[ Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) 

### Solution 1 BFS,Iterative
#### Idea:
The same as Q102 BFS method, and store the element at the end position of this level.
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
    public List<Integer> rightSideView(TreeNode root) {
        Queue<TreeNode> q=new LinkedList<TreeNode>();
        List<Integer> list=new ArrayList<>();
        if (root==null) return list;
        int level=1,cout;
        q.offer(root);
        while(!q.isEmpty()){
          cout=0;
          while(level>0){
            TreeNode tmp=q.poll();
            if(level==1) list.add(tmp.val);
            if(tmp.left!=null){cout++;q.offer(tmp.left);}
            if(tmp.right!=null){cout++;q.offer(tmp.right);}
            level--;
          }
            level=cout;
        }
                         
        return list;
    }
}
```
#### Reference:

---

