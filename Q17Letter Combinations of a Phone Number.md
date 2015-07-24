## Q17[Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) 

### Solution 1 Backtrack
#### Idea:
In backtrack use a pointer "cur" to mark current letter position for back process. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
//The code length can be compressed by using a map for icon information.

public class Solution {
    List<String> l=new ArrayList<String>();
    public List<String> letterCombinations(String digits) {
        if(digits.length()==0) return l;
        StringBuilder s=new StringBuilder();
        backtrack(0,digits.length(),digits,s);
        return l;
    }
    void backtrack(int cur,int n,String digits,StringBuilder s){
       if(cur==n) {l.add(s.toString()); return;}
       int num=digits.charAt(cur)-'0';
       if(num==1) backtrack(cur+1,n,digits,s);
       else if(num==0){
           s.append(' ');
           backtrack(cur+1,n,digits,s);
           s.deleteCharAt(cur);
       }
       else if(num <= 6){
           for(int i=0;i<3;i++){
               s.append((char)('a'+(num-2)*3+i));
               backtrack(cur+1,n,digits,s);
               s.deleteCharAt(cur);
           }
       }
       else if(num==7){
            for(int i=0;i<4;i++){
               s.append((char)('p'+i));
               backtrack(cur+1,n,digits,s);
               s.deleteCharAt(cur);
            }  
       }
       else if(num==8){
            for(int i=0;i<3;i++){
               s.append((char)('t'+i));
               backtrack(cur+1,n,digits,s);
               s.deleteCharAt(cur);
            }
       }
       else if(num==9){
            for(int i=0;i<4;i++){
               s.append((char)('w'+i));
               backtrack(cur+1,n,digits,s);
               s.deleteCharAt(cur);
            }
       }
    }
}     
```
#### Reference:

---

