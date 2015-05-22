## Q106 [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/) 

### Solution 1 Recursive
#### Idea:
 The same as Q105, adjust parameters.
 
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {

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
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        if (postorder.length == 0) return null;
        return buildTree(postorder, inorder, postorder.length- 1, 0, inorder.length - 1);
    }

    private TreeNode buildTree(int[] postorder, int[] inorder, int postorderIndex, int start, int end) {
        if (start > end) return null;
        TreeNode node = new TreeNode(postorder[postorderIndex]);
        int inorderIndex = findInorderIndex(inorder, start, end, postorder[postorderIndex]);
        int leftTreeSize = inorderIndex - start;
        int rightTreeSize = end - inorderIndex;
    node.right = buildTree(postorder, inorder, postorderIndex-1, inorderIndex + 1, end); 
    node.left = buildTree(postorder, inorder, postorderIndex -rightTreeSize - 1, start, inorderIndex - 1);
        return node;
    }
     
    private int findInorderIndex(int[] inorder, int start, int end, int key) {
        for (int i = start; i <= end; i++) {
            if (inorder[i] == key) return i;
        }
        return -1;
    }
}


```
#### Reference:

---

