## Q132[Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/) 

### Solution 1 DP
#### Idea:
The cut[i] suggest the cut amount of subString s from 0 to i.
For each element in String consider palindrome in odd or even situation meanwhile update cut[].  
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int minCut(String S) {
        int n = S.length();
        char[] s=S.toCharArray();
        int[] cut=new int[n];  // number of cuts for the first k characters
        for (int i = 1; i <n; i++) {
            cut[i] = i;
        }
        for (int i = 0; i < n; i++) {
        
            // odd length palindrome,s[i] is middle
            for (int j = 0; i-j>=0 && i+j < n && s[i-j]==s[i+j] ; j++) {
               if(i-j-1==-1) cut[i+j] = 0; //s[0~i+j] is palindrome
               else cut[i+j] = Math.min(cut[i+j],1+cut[i-j-1]);
            }
            
            // even length palindrome,s[i] is rear of left part
            for (int j = 1; i-j+1>=0 && i+j < n && s[i-j+1] == s[i+j]; j++){
                if(i-j==-1) cut[i+j] = 0; //s[0~i+j] is palindrome
                else cut[i+j] = Math.min(cut[i+j],1+cut[i-j]);
            }
        }
        return cut[n-1];
    }
}
```
#### Reference:
---

