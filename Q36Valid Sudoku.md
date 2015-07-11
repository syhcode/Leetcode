## Q36[Valid Sudoku](https://leetcode.com/problems/valid-sudoku/) 

### Solution 1 Hashmap
#### Idea:
Build the HashMap<Character,HashMap<Integer,Integer>>, 
the HashMap<Integer,Integer> is to store the  same character's different column and row index.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n^2)
#### Source code:
```
public class Solution {
    public boolean isValidSudoku(char[][] board) {
        int n=board.length;
        Map<Character,HashMap<Integer,Integer>> map=new HashMap<Character,HashMap<Integer,Integer>>();
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(board[i][j]=='.') continue;
                if(map.containsKey(board[i][j])){
                    HashMap<Integer,Integer> tmp=map.get(board[i][j]);
                    if (tmp.containsKey(i)) return false;  //row no duplication
                    else{
                      for(int val:tmp.keySet()){
                        if(tmp.get(val)==j) return false;  // column no duplication
                        if(val/3==i/3&&tmp.get(val)/3==j/3) return false; // smaller block no duplication
                      }
                      tmp.put(i,j);
                    }
                }
                else{ 
                HashMap<Integer,Integer> inmap=new HashMap<Integer,Integer>();
                inmap.put(i,j);
                map.put(board[i][j],inmap);
                }
            }
        }
        return true;
    }
}
```
#### Reference:
[Java map traversal](http://www.trinea.cn/android/hashmap-loop-performance/)
---

