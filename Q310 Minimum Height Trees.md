## Q310[Minimum Height Trees](https://leetcode.com/problems/minimum-height-trees/) 

### Solution 1 Backtrack (TLE)
#### Idea: 
count the max depth for each start node, find the smallest.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        HashSet<Integer> set = new  HashSet<Integer>();
        List<Integer> res = new ArrayList<Integer>();
        int min = Integer.MAX_VALUE;
        for(int i=0;i<n;i++){
            int temp=depth(i,edges,set);
            if (min>temp){
                res.clear();
                res.add(i);
                min=temp;
            }else if(min==temp) res.add(i);
        }
        return res;
    }
    public int depth(int root, int[][] edges,HashSet<Integer> set){ // find max depth for each node
        int min= Integer.MIN_VALUE;
        for(int i=0;i<edges.length;i++){
            for(int j=0;j<edges[0].length;j++){
                if(edges[i][j]==root && !set.contains(edges[i][j^1])){
                   set.add(root);
                   min=Math.max((1+depth (edges[i][j^1],edges,set)),min);
                   set.remove(root);
                }   
            }
        }
        return min==Integer.MAX_VALUE?1:min;
    }
}
```
#### Reference:

---

### Solution 2 BFS, graph 
#### Idea: 
the degree for the leaves is 1, each time remove all leaves and reveal all new leaves, finally result in two or one leaf.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public List<Integer> findMinHeightTrees(int n, int[][] edges) {
     if (n == 1) return Collections.singletonList(0);

    List<Set<Integer>> adj = new ArrayList<>(n);
    for (int i = 0; i < n; ++i) adj.add(new HashSet<>());
    for (int[] edge : edges) {
        adj.get(edge[0]).add(edge[1]);
        adj.get(edge[1]).add(edge[0]);
    }
    List<Integer> leaves = new ArrayList<>();
    for (int i = 0; i < n; ++i)
        if (adj.get(i).size() == 1) leaves.add(i);

    while (n > 2) {
        n -= leaves.size();
        List<Integer> newLeaves = new ArrayList<>();
        for (int i : leaves) {
            int j = adj.get(i).iterator().next(); // get set's first element
            adj.get(j).remove(i);
            if (adj.get(j).size() == 1) newLeaves.add(j); //size could be 0 after loop
        }
        leaves = newLeaves;
    }
    return leaves;
  }
}
```
#### Reference:
BFS method [https://leetcode.com/discuss/71763/share-some-thoughts]
---

