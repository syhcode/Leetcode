## Q36[Valid Sudoku](https://leetcode.com/problems/valid-sudoku/) 

### Solution 1 Backtracking
#### Idea:
Backtracking by deal with current change and judge if it is the final answer, if not do backtracking process. 
The boolean backtrack method itself searches possible answer and makes judgment of answer. 
#### Time Complexity: 
O(9^(n*n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void solveSudoku(char[][] board) {
        solve(board);
    }

    public boolean solve(char[][] board){
        for(int i = 0; i < board.length; i++){
            for(int j = 0; j < board.length; j++){
                if(board[i][j] == '.'){
                    for(char c = '1'; c <= '9'; c++){//trial. Try 1 through 9 for each cell
                        if(isValid(board, i, j, c)){
                            board[i][j] = c; //Put c for this cell

                            if(solve(board))
                                return true; //If it's the solution return true
                            else
                                board[i][j] = '.'; //Otherwise go back
                        }
                    }
                    return false; //since this time '.' is changed but not checked.
                }
            }
        }
        return true; // no '.' exist is an answer.
    }

    public boolean isValid(char[][] board, int i, int j, char c){
        //Check colum
        for(int row = 0; row < 9; row++)
            if(board[row][j] == c)
                return false;

        //Check row
        for(int col = 0; col < 9; col++)
            if(board[i][col] == c)
                return false;

        //Check 3 x 3 block
        for(int row = (i / 3) * 3; row < (i / 3) * 3 + 3; row++)
            for(int col = (j / 3) * 3; col < (j / 3) * 3 + 3; col++)
                if(board[row][col] == c)
                    return false;
        return true;
    }
}
```
#### Reference:

---

