## Q224[Basic Calculator ](https://leetcode.com/problems/basic-calculator/) 

### Solution 1 Iterative 
#### Idea:
When meet digits form them into a number, when meet '+','-' update the former result and sign,when meet '('
push the former sign and result in stack, when meet ')' update the result in parenthesis, then pop former sign and result from stack,
and do sum of former result and result in parenthesis. Finally add the number in rear.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public int calculate(String s) {
    Stack<Integer> stack = new Stack<Integer>();
    int result = 0;
    int number = 0;
    int sign = 1;
    for(int i = 0; i < s.length(); i++){
        char c = s.charAt(i);
        if(Character.isDigit(c)){
            number = 10 * number + (int)(c - '0');
        }else if(c == '+'){
            result += sign * number;
            number = 0;
            sign = 1;
        }else if(c == '-'){
            result += sign * number;
            number = 0;
            sign = -1;
        }else if(c == '('){
            //save result,sign before parenthesis.
            stack.push(result);
            stack.push(sign);
            // reset sign and result for calculation in parenthesis.
            sign = 1;   
            result = 0;
        }else if(c == ')'){
            result += sign * number;
            //wait a new number after parenthesis.  
            number = 0; 
            //update result with former result,sign and result in parenthesis.
            result *= stack.pop();    
            result += stack.pop();   

        }
    }
    result += sign * number;
    return result;
  }

}
```
#### Reference:

---

