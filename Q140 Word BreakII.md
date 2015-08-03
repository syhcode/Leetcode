## Q140[Word Break II](https://leetcode.com/problems/word-break-ii/) 

### Solution 1 Recursive & DP
#### Idea:
Backtrack depending on Q139 DP method,however when input"aaaa...aab","a" "a..a"..get TLE.
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
public class Solution {
    List<String> l=new ArrayList<String>();
    public  List<String> wordBreak(String s, Set<String> wordDict) {
		if(s.length()==0||wordDict.isEmpty()) return l;
		StringBuilder sb=new StringBuilder();
	    boolean[] dp = new boolean[s.length() + 1];
		dp[0] = true;
	    backtrack(s,wordDict,0,1,sb,dp);
		return l;
	}
	void backtrack(String s,Set<String> wordDict,int left, int right,StringBuilder sb,boolean[] dp){
        if(right==s.length()+1){
		    if(dp[right-1]==true)
			l.add(new String(sb.toString().trim()));
			return;
		}
		for(int j=left; j < right; j++){
			if(dp[j] && wordDict.contains(s.substring(j, right))){
			     dp[right] = true;
			     sb.append(s.substring(j, right)+' ');
			     backtrack(s,wordDict,right,right+1,sb,dp);
			     dp[right]=false;
			     for(int k=j;k<right+1;k++)
			       sb.deleteCharAt(sb.length()-1);
	      	}
		}
		backtrack(s,wordDict,left,right+1,sb,dp);  
	}
}
```
#### Reference:
---

