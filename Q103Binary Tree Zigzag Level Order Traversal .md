## Q103[Binary Tree Zigzag Level Order Traversal ](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) 

### Solution 1 Iterative 
#### Idea:
BFS using queue, judging the marker and change the output order for each level;
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        Deque<TreeNode> dq=new LinkedList<TreeNode>();
        if(root==null) return res;
        dq.offer(root);
        int count=0;
        while (!dq.isEmpty()){
            int size=dq.size();  
            List<Integer> list =new LinkedList<Integer>();
            for(int i=0;i<size;i++){
                TreeNode temp=dq.poll();  
                if(temp.left!=null) dq.offer(temp.left); 
                if(temp.right!=null) dq.offer(temp.right);
                if(count==0) list.add(temp.val); 
                else list.add(0,temp.val);
            }
            count^=1;
            res.add(list); 
        }
        return res;
    }
}
```
#### Reference:

---

