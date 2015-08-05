## Q52[N-Queens II](https://leetcode.com/problems/n-queens-ii/) 

### Solution 1 Backtrack
#### Idea:
Just simplify Q51.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    int total=0;
    public  int totalNQueens(int n) {
	    StringBuilder sb=new StringBuilder();
		HashSet<Integer> col= new HashSet<Integer>();
	    HashSet<Integer> slope1= new HashSet<Integer>();
		HashSet<Integer> slope2= new HashSet<Integer>();
		for(int i=0;i<n;i++) {sb.append('.');}
		backtrack(sb,0,n,col,slope1,slope2);
	    return total;
	}
	void backtrack(StringBuilder sb,int row,int n,HashSet<Integer> col,
	                        HashSet<Integer> slope1,HashSet<Integer> slope2){
		if(row==n){
		    total++;
			return;
		}
		for(int i=0;i<n;i++){
			if(!col.contains(i)&&!slope1.contains(i-row)&&!slope2.contains(i+row)){
			    col.add(i);slope1.add(i-row);slope2.add(i+row);
			    backtrack(sb,row+1,n,col,slope1,slope2);
			    col.remove(i); slope1.remove(i-row);slope2.remove(i+row);   
		    }
		}
    }
}
```
#### Reference:
---

