## Q223[Rectangle Area](https://leetcode.com/problems/rectangle-area/) 

### Solution 1
#### Idea:
Analysis if they are overlapped , partly overlapped ,or one cover another.
#### Time Complexity: 
O(1)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int area1=(C-A)*(D-B);
        int area2=(G-E)*(H-F);
        int bottom=C-A+G-E>Math.max((G-A),(C-E))?C-A+G-E-    // overlap or not
          ( (A-E)*(G-C)>0?Math.max((C-A),(G-E)):Math.max((G-A),(C-E)) ):0; //whole or partly
        int height=D-B+H-F>Math.max((D-F),(H-B))?D-B+H-F-
          ( (D-H)*(F-B)>0?Math.max((D-B),(H-F)):Math.max((D-F),(H-B)) ):0;
        return area1+area2-bottom*height;
    }
}
```
#### Reference:
---

