## Q173[ Binary Search Tree Iterator  ](https://leetcode.com/problems/binary-search-tree-iterator/) 

### Solution 1 Stack,Iterative
#### Idea:
The next() is to realize in-order traversal.First store all left children and root in stack,when pop out a element,push in its right child( as sub-root)  and the right's all left elements in stack.  
#### Time Complexity: 
O(1)  :just pop from current stack
#### Space Complexity:
O(h)  :store all the left elements
#### Source code:
```
/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

public class BSTIterator {

    private Stack<TreeNode> stack=new Stack<>();
    public BSTIterator(TreeNode root) {
        TreeNode cur = root;
        while(cur != null){
            stack.push(cur);
            if(cur.left != null)
                cur = cur.left;
            else
                break;
        }
    }

    /** @return whether we have a next smallest number */
    public boolean hasNext() {
    
        return !stack.isEmpty();
    }

    /** @return the next smallest number */
    public int next() {
        TreeNode node = stack.pop();
        TreeNode cur = node;
           // traversal right branch,get all left elements and sub-root.
        if(cur.right != null){
            cur = cur.right;
            while(cur != null){
                stack.push(cur);
                if(cur.left != null)
                    cur = cur.left;
                else
                    break;
            }
        }
        return node.val;
    }
}

/**
 * Your BSTIterator will be called like this:
 * BSTIterator i = new BSTIterator(root);
 * while (i.hasNext()) v[f()] = i.next();
 */
```
#### Reference:

---

