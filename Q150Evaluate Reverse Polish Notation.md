## Q150[ Evaluate Reverse Polish Notation ](https://leetcode.com/problems/evaluate-reverse-polish-notation/) 

### Solution 1 stack
#### Idea:
When meet a number, push it in stack; when meet a operator, pop two numbers and calculate, then push result of calculation in stack.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int evalRPN(String[] tokens) {
    Stack<Integer> stack = new Stack <>();
    for (int i=0; i < tokens.length; i++) {
        String token = tokens[i];
        if ( isOperation ( token ) ) {
            int val2 = stack.pop();
            int val1 = stack.pop();
            int tmp = performOperation ( token,  val1, val2);
            stack.push(tmp);
        }else
            stack.push(Integer.parseInt(token));
    }
    return stack.peek();
  }
  public boolean isOperation ( String s) {
    return (s.equals("+") || s.equals("-") || s.equals("/") || s.equals("*"));
  }
  public int performOperation ( String op, int val1, int val2) {
    int res=0;
    if(op.equals("+") ) { res = val1 + val2; }
    else if(op.equals("-") ) { res = val1 - val2; }
    else if(op.equals("/") ) { 
        if(val2==0) return  Integer.MAX_VALUE;
        res = val1 / val2;
    }
    else if(op.equals("*") ) { res = val1 * val2; }
    return res;
  }
}
```
#### Reference:

---

