## Q108[ Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/) 

### Solution 1 Recursive
#### Idea:
Get the mid in array as sub-root in BST each level, doing the process recursively. 
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
    public TreeNode sortedArrayToBST(int[] nums) {
        if(nums.length==0) return null;
        TreeNode root=f(nums,0,nums.length-1);
        return root;
    }
    TreeNode f(int[] nums,int low,int high){
        if(low>high) return null;
        int mid=(low+high)/2;
        TreeNode newnode=new TreeNode(nums[mid]);
        newnode.left=f(nums,low,mid-1);
        newnode.right=f(nums,mid+1,high);
        return newnode;
    }
}
```
#### Reference:

---

