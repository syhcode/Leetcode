## Q133[Clone Graph](https://leetcode.com/problems/clone-graph/) 

### Solution 1 Recursive,DFS
#### Idea:
Clone root and its neighbors List in DFS.When meet a visited node, return the built copy for this node. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for undirected graph.
 * class UndirectedGraphNode {
 *     int label;
 *     List<UndirectedGraphNode> neighbors;
 *     UndirectedGraphNode(int x) { label = x; neighbors = new ArrayList<UndirectedGraphNode>(); }
 * };
 */
public class Solution { 
    HashMap<UndirectedGraphNode,UndirectedGraphNode> map = new HashMap<UndirectedGraphNode,UndirectedGraphNode>();
    public UndirectedGraphNode cloneGraph(UndirectedGraphNode node) {
        if(node==null) return null;
        UndirectedGraphNode root = new  UndirectedGraphNode(node.label);
        if(map.containsKey(node)) return map.get(node);
        map.put(node,root);
        for(int i=0;i<node.neighbors.size();i++){
              root.neighbors.add(cloneGraph(node.neighbors.get(i)));
        }
        return root;
    }
}
```
#### Reference:
---

