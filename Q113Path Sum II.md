## Q113[Path Sum II](https://leetcode.com/problems/path-sum-ii/) 
### Solution 1 Backtracking
#### Idea:
Use Backtracking method to deal with each level.Build a original list to store the elements that is formerly traversed,
when find the a answer, copy the current list and add it to the final result lists,and then continue backtracking.
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
    List<List<Integer>> lists= new ArrayList<List<Integer>>();
    
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        if(root==null) return lists;
        List<Integer> list=new ArrayList<Integer>();
        backtrack(root,sum,list);
        return lists;
    }
    void backtrack(TreeNode root,int sum, List<Integer> list){
        if(root==null) return;
        list.add(root.val);
        if(root.left==null&&root.right==null&&sum==root.val){
            List<Integer> newlist=new ArrayList<Integer>(list);
            lists.add(newlist);
        }    
        else{
        backtrack(root.left,sum-root.val,list);
        backtrack(root.right,sum-root.val,list);
        }
        list.remove(list.size()-1);
    }
}
```
#### Reference:

---

