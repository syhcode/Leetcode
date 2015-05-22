## Q105 [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) 

### Solution 1 Recursive
#### Idea:
based on preorder,the first element of preorder(rootnode) found in inorder divide array in two parts,rootnode left part and right part,
then build NEW Preorder And Inorder for each part,and in the same way treat the left part and right part respectively and recursively. 
eg. pre[654879] in[456789] processed to [45]6[789] processed to [[4]5]6[[7]8[9]].
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
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if (preorder.length == 0) return null;
        return buildTree(preorder, inorder, 0, 0, inorder.length - 1);
    }

//in build Tree ,preorderindex is corresponding begin of left or right part element,start and end is range for corresponding-part inoreder index. 

    private TreeNode buildTree(int[] preorder, int[] inorder, int preorderIndex, int start, int end) {  
        if (start > end) return null;
        TreeNode node = new TreeNode(preorder[preorderIndex]);
        int inorderIndex = findInorderIndex(inorder, start, end, preorder[preorderIndex]);
        int leftTreeSize = inorderIndex - start;
        int rightTreeSize = end - inorderIndex;
        
        // reset  the inorder and preorder for corresponding parts.
    node.left = buildTree(preorder, inorder, preorderIndex + 1, start, inorderIndex - 1);   //left part,divided by preorder[preorderindex]
    node.right = buildTree(preorder, inorder, preorderIndex + leftTreeSize + 1, inorderIndex + 1, end);  // right part,divided by partpreorder[preorderindex]
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

