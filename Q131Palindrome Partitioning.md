## Q131[Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/) 

### Solution 1 Backtrack
#### Idea:
Try to find a Palindrome substring and begin to search the remained string palindrome combination.
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
public class Solution {
    List<List<String>> lists=new ArrayList<List<String>>();
    List<String> list =new ArrayList<String>();
    public List<List<String>> partition(String s) {
        if(s.length()==0) return lists;
        helper(s,0);
        return lists;
    }
    void helper(String s,int cur){
		StringBuilder sb=new StringBuilder();
        if(cur==s.length()){	
            List<String> newlist =new ArrayList<String>(list);  
			lists.add(newlist);   
			 return;
		}
		for(int i=cur;i<s.length();i++){
			sb.append(s.charAt(i));
			if(isValid(sb.toString())){
			   list.add(sb.toString());
			   helper(s,i+1); 
			   list.remove(list.size()-1);
			}
		}
	}
	static boolean isValid(String s){
	    int i=0,j=s.length()-1;
		while(i<=j){
		  char c1=s.charAt(i),c2=s.charAt(j);
		  if(c1==c2) {i++;j--;}
		  else return false;
		}
	    return true;
	}
}
```
#### Reference:

---

