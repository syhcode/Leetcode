## Q297[Serialize and Deserialize Binary Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/) 

### Solution: Divided and Conquer
#### Idea: 
use pre-order traversal to serialize tree, "#" stand for null value;
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Codec {
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder sb =new StringBuilder();
        if(root==null) return "#";
        sb.append(Integer.toString(root.val)+","+serialize(root.left)+","+serialize(root.right));
        return sb.toString();
    }
    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        Deque<String> nodes = new LinkedList<String>(Arrays.asList(data.split(",")));
        return buildTree(nodes);
    }
    private TreeNode buildTree(Deque<String> nodes) {
        String val = nodes.poll();
        if (val.equals("#")) return null; // this root is null
        else {
            TreeNode node = new TreeNode(Integer.valueOf(val));
            node.left = buildTree(nodes); //terminate for '#'
            node.right = buildTree(nodes);
            return node;
        }
    }
    
}

```
#### Reference:
similar with: Q331[ Verify Preorder Serialization of a Binary Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/) 

---

