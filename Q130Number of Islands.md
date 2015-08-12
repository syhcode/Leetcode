## Q130[Number of Islands](https://leetcode.com/problems/number-of-islands/) 

### Solution 1 BFS,Queue
#### Idea:
Mark edge 'O' with '+' first, then mark all '0' area end at edge with '+', finally replace '+' with 'O' and
replace 'O' with '+' in the graph.  
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public void solve(char[][] board) {
        if (board.length == 0) return;
        int rowN = board.length;
        int colN = board[0].length;
        Queue<Point> queue = new LinkedList<Point>();
        //mark edge '0' as '+' that will be replaced by 'O'
        
        for(int i=0;i<rowN;i++)
            for(int j=0;j<colN;j++)
                if(i==0||i==rowN-1||j==0||j==colN-1)
                    if(board[i][j]=='O') {
                        board[i][j]='+';
                        queue.offer(new Point(i,j));
                    }
                    
        //BFS for the 'O's, and mark it as '+'
        while (!queue.isEmpty()){
            Point p = queue.poll();
            int row = p.x;
            int col = p.y;
            if (row - 1 >= 0 && board[row-1][col] == 'O') {
                board[row-1][col] = '+'; queue.add(new Point(row-1, col));
            }
            if (row + 1 < rowN && board[row+1][col] == 'O') {
                board[row+1][col] = '+'; queue.add(new Point(row+1, col));
            }
            if (col - 1 >= 0 && board[row][col - 1] == 'O') {
                board[row][col-1] = '+'; queue.add(new Point(row, col-1));
            }
            if (col + 1 < colN && board[row][col + 1] == 'O') {
                board[row][col+1] = '+'; queue.add(new Point(row, col+1));
            }                
        }
        //turn all '+' to 'O', and 'O' to 'X'
        for (int i = 0; i<rowN; i++){
            for (int j=0; j<colN; j++){
                if (board[i][j] == 'O') board[i][j] = 'X';
                if (board[i][j] == '+') board[i][j] = 'O';
            }
        }
    }
}

```
#### Reference:
---

