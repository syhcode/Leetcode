## Q99[Recover Binary Search Tree](https://leetcode.com/problems/recover-binary-search-tree/) 

### Solution 1 Morris Traversal
#### Idea:
The in-order Morris Traversal use "temp" for build loop before back traversal and destroy loop after traversal, 
the pointer "cur" traverse in-oreder. Judge tree's in order traversal sequence and recover the original BST.  
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
    public void recoverTree(TreeNode root) {
        TreeNode former = null;
        TreeNode first = null, second = null;
        TreeNode temp = null;
        TreeNode cur = root;
        
        while(cur!=null){
            if(cur.left!=null){
                temp = cur.left;
                while(temp.right!=null && temp.right != cur)
                    temp = temp.right;
                if(temp.right!=null){
 // /- - - - - - - - - - - - - - - - - - - - - - - - - judge in-order traversal sequence\             
                    if(former!=null && former.val > cur.val){                
                        if(first==null){first = former;second = cur;}
                        else{second = cur;}
                    }
                    former = cur;
 // \- - - - - - - - - - - - - - - - - - - - - - - - - judge in-order traversal sequence/   
                    temp.right = null;
                    cur = cur.right;
                }else{
                    temp.right = cur;
                    cur = cur.left;
                }
            }else{
 //  /- - - - - - - - - - - - - - - - - - - - - - - - -judge in-order traversal sequence\            
                if(former!=null && former.val >cur.val){
                    if(first==null){first = former;second = cur;}
                    else{second = cur;}
                }
               former = cur;
 //  \- - - - - - - - - - - - - - - - - - - - - - - - -judge in-order traversal sequence/            
                cur = cur.right;
            }
        }
        
        
        // swap two node values;
        if(first!= null && second != null){
            int t = first.val;
            first.val = second.val;
            second.val = t;
        }
    }
}
```
#### Reference:
[]()
[Morris Traversal](http://www.cnblogs.com/AnnieKim/archive/2013/06/15/morristraversal.html),,,  
[In-order traversal Space(n) solution](https://leetcode.com/discuss/13034/no-fancy-algorithm-just-simple-and-powerful-order-traversal)

