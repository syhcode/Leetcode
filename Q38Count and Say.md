## Q38[Count and Say](https://leetcode.com/problems/count-and-say/) 

### Solution 1 Recursive
#### Idea:
In rear recursively process next level from n.Pay attention to string index bound in loop.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public String countAndSay(int n) {
        if(n==0) return null;
        StringBuilder s=new StringBuilder();
        s.append('1'); 
        return helper(1,n,s);
    }
    String helper(int begin,int end,StringBuilder s){
        if(begin==end) return s.toString();
        String tmp=s.toString();
        int i=0;
        char c=tmp.charAt(0);
        StringBuilder cur =new StringBuilder();
        while(i<tmp.length()){
            c=s.charAt(i);
            int count=0;
            while(i<tmp.length()&&s.charAt(i)==c){
                i++;
                count++;
            }
            cur.append(String.valueOf(count)+c);
        }
        return helper(begin+1,end,cur);
    }
}
```
#### Reference:

---

