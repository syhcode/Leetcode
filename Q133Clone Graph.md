## Q133[Clone Graph](https://leetcode.com/problems/clone-graph/) 

### Solution 1 Recursive,DFS
#### Idea:
Clone root and its neighbors List in DFS. Only this adjacent root node's graph can be tracked, and it may not a completed graph
if there is another parallel adjacent root node. 
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
    private HashMap<Integer, UndirectedGraphNode> map = new HashMap<>();
    public UndirectedGraphNode cloneGraph(UndirectedGraphNode node) {
        if (node == null) return null;
        return clone(node);
    }

    private UndirectedGraphNode clone(UndirectedGraphNode node) {
        if (map.containsKey(node.label)) return map.get(node.label);// has a cycle
        
        UndirectedGraphNode copyNode = new UndirectedGraphNode(node.label);
        map.put(copyNode.label, copyNode);
        for (UndirectedGraphNode tmp : node.neighbors) {
            copyNode.neighbors.add(clone(tmp));
        }
        return copyNode;
    }
}
```
#### Reference:
---

