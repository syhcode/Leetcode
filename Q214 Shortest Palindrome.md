## Q214[Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/) 

### Solution 1 Recursive
#### Idea:
KMP is a method to do string match process.The first step is to make a pretreatment of the target String,making
an prefix array to mark the every string element's prefix match position. Then when judge a element not matching with
original string,depending on the former element's prefix information move the target string forward until match the prefix.
In this question,just make a mirror of target string and solve the problem depending on its prefix array.
   
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public String shortestPalindrome(String s) {
        if(s.length() <= 1){ return s; }
        String curs = s + " " + new StringBuilder(s).reverse().toString();
        
        //KMP Algorithm- - - - - - - - - - - - - - - - - -
        //initiate arrayPrx all 0;
        int[] arrayPrx = new int[curs.length()];
        for(int i = 1 ; i < curs.length() ; i++){
            //depend on former ele's prefix to match the prefix in new position.
            int prefix = arrayPrx[i-1];
            while(prefix > 0 && curs.charAt(prefix) != curs.charAt(i)){
                prefix = arrayPrx[prefix-1];
            }
            if(curs.charAt(prefix) == curs.charAt(i)){
                arrayPrx[i] = prefix+1;
            }
        }
        //- - - - - - - - - - - - - - - - - - - - - - - - - - -  
        
        return new StringBuilder(s.substring(dupPrx[curs.length()-1])).reverse().toString() + s;
    }
}

```
#### Reference:

---

