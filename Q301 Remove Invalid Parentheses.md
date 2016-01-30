## Q301 [Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/) 

### Solution 1 Backtrack
#### Idea:
Judge how many '(' and ')' need remove (marked as dupL,dupR), then do the DFS backtrack. 
#### Time Complexity:
O(2^n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<String> removeInvalidParentheses(String s) {
        Set<String> res = new HashSet<String>();
        StringBuilder sb = new StringBuilder();
        int dupL=0,dupR=0;
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='(') dupL++;
            if(s.charAt(i)==')'){
                if(dupL<=0) dupR++;
                else dupL--;
            }
        }
        helper(s,res,sb,dupL,dupR,0,0);
        return new ArrayList<String>(res);
    }
    void helper(String s,Set<String> res,StringBuilder sb,int dupL,int dupR,int begin,int check){
        if(begin == s.length() && check==0 && dupL==0 && dupR==0){
            res.add(sb.toString()); 
            return;
        }
        if(begin==s.length()|| check<0 || dupL<0 || dupR<0) return;
        
      if(s.charAt(begin)=='('){
                sb.append('(');
                helper(s,res,sb,dupL,dupR,begin+1,check+1);
                sb.deleteCharAt(sb.length()-1);
                helper(s,res,sb,dupL-1,dupR,begin+1,check);
      }
      else if(s.charAt(begin)==')'){
                sb.append(')');
                helper(s,res,sb,dupL,dupR,begin+1,check-1);
                sb.deleteCharAt(sb.length()-1);
                helper(s,res,sb,dupL,dupR-1,begin+1,check);
      }
      else  {
                sb.append(s.charAt(begin));
                helper(s,res,sb,dupL,dupR,begin+1,check);
                sb.deleteCharAt(sb.length()-1);
      }
    
    }
}


```
#### Reference:

---

