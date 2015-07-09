## Q116[Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/) 
## Q117[Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/) 
### Solution 1 Iterative
#### Idea:
Use normal BFS method link each elements.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for binary tree with next pointer.
 * public class TreeLinkNode {
 *     int val;
 *     TreeLinkNode left, right, next;
 *     TreeLinkNode(int x) { val = x; }
 * }
 */
public class Solution {
    public void connect(TreeLinkNode root) {
        Queue<TreeLinkNode > q=new LinkedList<TreeLinkNode >();
        if (root==null) return ;
        int level=1,cout;
        q.offer(root);
        while(!q.isEmpty()){
          cout=0;
          while(level>0){
            TreeLinkNode  tmp=q.poll();
            level--;
            if(tmp.left!=null){cout++;q.offer(tmp.left);}
            if(tmp.right!=null){cout++;q.offer(tmp.right);}
            if(level==0) tmp.next=null;
            else{
            TreeLinkNode  tmp1=q.peek(); //Get first(head) ele in queue structure.
            tmp.next=tmp1;
            tmp=tmp1;
            }
          }
            level=cout;
        }
    }
}
```
#### Reference:

---

