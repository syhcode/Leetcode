## Q174[Dungeon Game](https://leetcode.com/problems/dungeon-game/) 

### Solution 1 DP
#### Idea:
From end to start point do DP reversely.
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(mn)
#### Source code:
```
public class Solution {
    public int calculateMinimumHP(int[][] dungeon) {
    if (dungeon.length == 0 ||dungeon[0].length == 0) return 0;
    int m=dungeon.length;
    int n=dungeon[0].length;

    int[][] health = new int[m+1][n+1];
    for(int i=0;i<m-1;i++) health[i][n]=Integer.MAX_VALUE;
    for(int j=0;j<n-1;j++) health[m][j]=Integer.MAX_VALUE;
    health[m - 1][n - 1] = Math.max(1 - dungeon[m - 1][n - 1], 1);
    for (int i= m-1; i >= 0; i--) {
        for (int j= n-1; j >= 0; j--) {
            if(i<m-1||j<n-1){
            int min = Math.min(health[i+1][j],health[i][j+1]);
            health[i][j]=Math.max(min-dungeon[i][j],1);
            }
        }
    }
    return health[0][0];
    }
}
```
#### Reference:

---

