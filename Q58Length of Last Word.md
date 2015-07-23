## Q58[Length of Last Word](https://leetcode.com/problems/length-of-last-word/) 

### Solution 1 
#### Idea:
In reversed order to process.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
   public static int lengthOfLastWord(String s) {
     if(s.length()==0) return 0;
	 int i=0,j=0;
	 // skip rear ' '.
	 while(j<s.length()){
		if(s.charAt(s.length()-1-j)==' ') j++;
		else break;
	}
	if(j==s.length()) return 0;
	for(i=0;j+i<s.length();i++){
		if(s.charAt(s.length()-1-j-i)==' '){
		  return i;
		}
	}   
	return i;
	}
}
```
#### Reference:

---

