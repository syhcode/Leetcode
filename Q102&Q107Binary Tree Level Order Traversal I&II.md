## Q102[ Binary Tree Level Order Traversal I](https://leetcode.com/problems/binary-tree-level-order-traversal/) 
## Q107[ Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/) 
### Solution 1 Queue,BFS
#### Idea:
Q102 and Q107 are exactly the same. Q102 use a queue to store each level's elements, meanwhile offer in next level's elements in the queue
based on current level elements' left and right, and meanwhile count next level's elements(as "cout"). 
Q107 just reverse the final lists or can add each element in reversed(add in front) order.
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> q=new LinkedList<TreeNode>();
        List<List<Integer>> lists=new ArrayList<List<Integer>>();
        if (root==null) return lists;
        int level=1,cout;
        q.offer(root);
        while(!q.isEmpty()){
          List<Integer> list=new ArrayList<>();
          cout=0;
          while(level>0){
            TreeNode tmp=q.poll();
            list.add(tmp.val);
            if(tmp.left!=null){cout++;q.offer(tmp.left);}
            if(tmp.right!=null){cout++;q.offer(tmp.right);}
            level--;
          }
            level=cout;
            lists.add(list);// For Q107: lists.add(0,list);
        }
                           //if not above,can append: Collections.reverse(lists);
        return lists;
    }
}
```
#### Reference:

---

