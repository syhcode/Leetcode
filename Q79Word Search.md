## Q79[Word Search](https://leetcode.com/problems/word-search/) 

### Solution Backtracking
#### Idea:
For each element in Matrix,use backtrack method to search its combinations that correspond to the searched word.
The backtrack searching method judge the current char and lead to further search.
#### Time Complexity:
O(4^mn)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean exist(char[][] board, String word) {
        
    for(int i = 0; i < board.length; i++)
        for(int j = 0; j < board[0].length; j++){
            if(search(board, i, j, word, 0))
                return true;
        }
    return false;
   }
    private boolean search(char[][] board, int i, int j, String word, int ind){
      if(ind == word.length()) return true;
      if(i > board.length-1 || i <0 || j<0 || j >board[0].length-1 || board[i][j]!=word.charAt(ind))
        return false;
      board[i][j]='*'; // mark to avoid later searching this element.
    
      boolean result =    search(board, i-1, j, word, ind+1) ||
                        search(board, i, j-1, word, ind+1) ||
                        search(board, i, j+1, word, ind+1) ||
                        search(board, i+1, j, word, ind+1);
                        
      board[i][j] = word.charAt(ind);  //recover origin matrix situation.
      return result;
        
    }
}
```
#### Reference:

---

