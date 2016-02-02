## Q331[ Verify Preorder Serialization of a Binary Tree](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/) 

### Solution  graph, vertex degree 
#### Idea: 
regard the tree as a graph,the preorder keep outdegree over indegree,finally reach 0;
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    //##4##13###629(posted order) = reverse : 926###31##4##(preorder start from right child)
    //#4#3#1#9#2#6# (in order)
    //for a number node, indegree+1 & outdegree+2, for the # node, indegree+1
    //degree = outdegree-indegree, the preorder keep outdegree over indegree,finally reach 0;
   
    public boolean isValidSerialization(String preorder) {
        String[] s = preorder.split(",");
        int degree=1;
        for(String temp:s){
            degree--;
            if (degree<0) return false;
            if(!temp.equals("#")) degree+=2
        }
        return degree==0;
    }
}

```
#### Reference:

---

