## Q22[Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) 

### Solution 1 Backtrack
#### Idea:
Since to process two target elements,in backtrack set two marks to check if any target reach it goal or backtrack
their values.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    List<String> l = new ArrayList<String>();
    StringBuffer sb=new StringBuffer();
    public List<String> generateParenthesis(int n) {
        helper(n,0,0);
        return l;
    }
    void helper(int n,int left,int right){
        if(right==n&&left==n){
            StringBuffer tmp=new StringBuffer(sb);
            l.add(tmp.toString());
            return;
        } 
        if(right>n||left>n) return;
        if(left<right) return;
        
        // two target elements backtrack.
        sb.append('(');
        // the remained levels 0 append to sb when back to this level
        helper(n,left+1,right);
        sb.deleteCharAt(sb.length()-1);
        sb.append(')');
        helper(n,left,right+1);
        sb.deleteCharAt(sb.length()-1);
    }
}
```
#### Reference:

---

