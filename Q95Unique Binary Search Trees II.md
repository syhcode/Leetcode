## Q95[Unique Binary Search Trees II ](https://leetcode.com/problems/unique-binary-search-trees-ii/) 

### Solution 1 Divided and Conquer
#### Idea:
Build a root's left and right BST List<TreeNode>,and build this root's left and right subtree depending on the roots in these two List<TreeNode>.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n^2)
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
  public List<TreeNode> generateTrees(int n) {
    return rootBuild(1, n);
}

  private List<TreeNode> rootBuild(int start, int end){
//many List<TreeNode> Builded in processing,but get the rootBuild(1,n) one. 
    List<TreeNode> res = new LinkedList<TreeNode>();
    if (start > end) {
        res.add(null); 
        return res;
    }

     for (int i = start; i <= end; ++i) {
        List<TreeNode> leftRoots = rootBuild(start, i - 1);
        List<TreeNode> rightRoots = rootBuild(i + 1, end);

        for (TreeNode left : leftRoots) {
            for (TreeNode right : rightRoots) {
                TreeNode root = new TreeNode(i);
                root.left = left;
                root.right = right;
                res.add(root);
            }
        }
     }
    return res;
  }
}
```
#### Reference:

---

