## Q14[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/) 

### Solution 1
#### Idea:
Initiate res of strs[0],then use later strs[i] to cut the different characters from res.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length==0) return "";
        String res=strs[0];
        for(int i=0;i<strs.length;i++)
        res=cutString(res,strs[i]);
        return res;
    }
    String cutString(String res,String s){
        int rear1=res.length();
		int rear2=s.length();
		for(int i=0;i<rear1;i++){
		   if(i>=rear2) {
		      res=res.substring(0,i);
		      break;
		   }
		   char tmp1=res.charAt(i);
		   char tmp2=s.charAt(i);
		   //can not use charAt() to compare directly
		   if(tmp1!=tmp2){
		      res=res.substring(0,i);
		      break;
		   }
		}
	return res;
	}
}    
```
#### Reference:
[String methods](http://blog.csdn.net/az44yao/article/details/7582580)
---

