## Q100[Same Tree](https://leetcode.com/problems/same-tree/) 

### Solution 1 Backtrack
#### Idea:
Check every row Q position by its row and column index relating to its left-right and right-left slope.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n^2)
#### Source code:
```
public class Solution {
    List<List<String>> list=new ArrayList<List<String>>();
    List<String> lists =new ArrayList<String>();
    public  List<List<String>> solveNQueens(int n) {
	    StringBuilder sb=new StringBuilder();
		HashSet<Integer> col= new HashSet<Integer>();
	    HashSet<Integer> slope1= new HashSet<Integer>();
		HashSet<Integer> slope2= new HashSet<Integer>();
		for(int i=0;i<n;i++) {sb.append('.');}
		backtrack(sb,0,n,col,slope1,slope2);
	    return list;
	}
	void backtrack(StringBuilder sb,int row,int n,HashSet<Integer> col,
	                        HashSet<Integer> slope1,HashSet<Integer> slope2){
		if(lists.size()==n){
		     list.add(new ArrayList<String>(lists));
			 return;
		}
		for(int i=0;i<n;i++)  {
			if(!col.contains(i)&&!slope1.contains(i-row)&&!slope2.contains(i+row)){
			    col.add(i);slope1.add(i-row);slope2.add(i+row);
			    sb.replace(i,i+1,"Q");		            
			    lists.add(sb.toString());
			    sb.replace(i,i+1,".");
			    backtrack(sb,row+1,n,col,slope1,slope2);
			    col.remove(i); slope1.remove(i-row);slope2.remove(i+row);   
			    lists.remove(lists.size()-1);
		    }
			    	   
		 }
			    
    }
}
```
#### Reference:
---

