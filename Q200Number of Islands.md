## Q200[Number of Islands](https://leetcode.com/problems/number-of-islands/) 

### Solution 1 Recursive
#### Idea:
When find a island, map out this island from the graph and start next search.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int numIslands(char[][] grid) {
        return search(grid,0);
    }
    int search(char[][] grid,int count){
        for(int i=0;i<grid.length;i++)
            for(int j=0;j<grid[0].length;j++){
                if(grid[i][j]=='1') {
                   return search(paint(grid,i,j),count+1);
                }
            }
        return count;
    }
    // map out found island.
    char[][] paint(char[][] grid,int row,int col){
        grid[row][col]='0';
        if(row+1<grid.length&&grid[row+1][col]=='1')
			 paint(grid,row+1,col);
		if(row-1>=0&&grid[row-1][col]=='1')
			 paint(grid,row-1,col);
		if(col+1<grid[0].length&&grid[row][col+1]=='1')
			 paint(grid,row,col+1);
		if(col-1>=0&&grid[row][col-1]=='1')
			 paint(grid,row,col-1);
		return grid;
    } 
}
```
#### Reference:
---

