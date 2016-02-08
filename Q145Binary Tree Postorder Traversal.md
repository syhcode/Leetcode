## Q145[ Binary Tree Postorder Traversal ](https://leetcode.com/problems/binary-tree-postorder-traversal/) 

### Solution 1 Recursive
#### Idea:
In each recursive traversal level, process this level and save this level's val in res.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res=new ArrayList<Integer>();
        postrun(root,res);
        return res;
    }
    void postrun(TreeNode root,List<Integer> res){
    	 if(root == null) return;
         postrun(root.left,res);
         postrun(root.right,res);
         res.add(root.val);
        
    }
}
```
### Solution 2 Iterative,stack
#### Idea:
postorder == reverse( preorder from right).
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> list = new LinkedList<Integer>();
        if(root == null) return list;
        Stack<TreeNode> sk = new Stack<TreeNode>();
        sk.push(root);
        list.add(0,root.val);
        while(!sk.isEmpty()){
            while(root.right!=null){
                root=root.right;
                list.add(0,root.val); // insert into first place
                sk.push(root);
            }
            TreeNode temp=sk.pop();
            if(temp.left!=null){
                root=temp.left;
                list.add(0,root.val);
                sk.push(root);
            }
        }
        return list;
    }
}
```

#### Reference:

---

