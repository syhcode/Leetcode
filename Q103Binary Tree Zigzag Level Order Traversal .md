## Q103[Binary Tree Zigzag Level Order Traversal ](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) 

### Solution 1 Iterative 
#### Idea:
Normal iterative Breadth-first Search method for binary tree. Depend on a QUEUE to store the next level elements (current left and right children) while popping 
the current tree node and storing the val in a list,then display this list(all val of this level) in normal order or in reversed order.
#### Time Complexity: 
O(2^n)
#### Space Complexity:
O(2^n)
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
  public List<List<Integer>> zigzagLevelOrder(TreeNode root) {

    List<List<Integer>> list = new ArrayList<List<Integer>>();
    Queue<TreeNode> q = new LinkedList<TreeNode>();
    int switchDirection = 0;

    if(root == null){
        return list;
    }
    q.offer(root);  //  "offer" is a add method for queue.

    while(!q.isEmpty()){
        List<Integer> l = new ArrayList<Integer>();
        int size = q.size();

        for(int i = 0; i < size; i++){
            TreeNode current = q.poll();
            l.add(current.val);

            if(current.right != null){
                q.offer(current.right);
            }
            if(current.left != null){
                q.offer(current.left);
            }
        }

        if(switchDirection % 2 == 0){
            Collections.reverse(l);
        }
        switchDirection++;
        list.add(l);
    }

    return list;
  }

}
```
#### Reference:

---

