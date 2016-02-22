## Q139[Word Break](https://leetcode.com/problems/word-break/) 

### Solution 1 DP
#### Idea:
Mark the end position of String section matching the dictWord, judge if the String match form head to end. 
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean wordBreak(String s, Set<String> wordDict) {  
        boolean[] mark = new boolean[s.length()+1];
        mark[0]=true;
        for(int i=0;i<s.length();i++){
            for(int j=i+1;j<=s.length();j++){
                String temp=s.substring(i,j);
                if( wordDict.contains(temp)&&mark[i] ) mark[j]=true;
            }
        }
        return mark[s.length()];  
    }
}
```
#### Reference:
---

