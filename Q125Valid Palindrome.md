## Q125[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) 

### Solution 1 Two Pointer
#### Idea:
Use two pointers initiating at start and end,then move to mid judging if the string is symmetric.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isPalindrome(String s) {
        int len=s.length();
        if(len==0) return true; 
        int p=0,q=s.length()-1;
        while(p<q){
        //only consider number or letter judging palindrome.
           while(p<len-1&&( !Character.isDigit(s.charAt(p))&&!Character.isLetter(s.charAt(p)) )) p++;
           while(q>0&&( !Character.isDigit(s.charAt(q))&&!Character.isLetter(s.charAt(q)) )) q--;
           if(p>=q) return true;
           if(s.charAt(p)==s.charAt(q)||Math.abs(s.charAt(p)-s.charAt(q))==32){
              p++;
              q--;
           }
           else return false;
        }
    return  true;  
    }
}
```
#### Reference:

---

