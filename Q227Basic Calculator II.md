## Q227[Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/) 

### Solution 1 Stack
#### Idea:
When meet a operation, save this operation bu do former operation's calculation.
For '+' or '-',push the later number*sign in stack,and for '-' or '*',pop out former result and do 
calculation with current number then push the result in stack.Finally do sum of all results in stack.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int calculate(String s) {
    int len;
    if(s==null || (len = s.length())==0) return 0;
    Stack<Integer> stack = new Stack<Integer>();
    int num = 0;
    char sign = '+';
    for(int i=0;i<len;i++){
        if(Character.isDigit(s.charAt(i))){
            num = num*10+s.charAt(i)-'0';
        }
        //when meet a operation,do former operation's calculation.
        if((!Character.isDigit(s.charAt(i)) &&s.charAt(i)!=' ') || i==len-1){
            if(sign=='-'){
                stack.push(num*-1);
            }
            if(sign=='+'){
                stack.push(num);
            }
            if(sign=='*'){
                stack.push(stack.pop()*num);
            }
            if(sign=='/'){
                stack.push(stack.pop()/num);
            }
            sign = s.charAt(i);
            num = 0;
        }
    }
    int res = 0;
    for(int i:stack){
        res += i;
    }
    return res;
  }
}
```
#### Reference:

---

