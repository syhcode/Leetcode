## Q32[Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/) 

### Solution Stack
#### Idea:
Define"()" is valid, and"(()" is half-valid,and"())..."is split by ')'.
The valid parentheses can finally pop out all'(',and sections of the valid are separated by ')'.
When meet ')' and stack is empty, set calculation basement position "left"=this ')' position,it split the valid sections;
When meet ')' and after pop() the stack is empty, we get a valid section and count length based on the "left".
When meet ')' and after pop() the stack is not empty,just count current half-valid section length by former '(' position.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int longestValidParentheses(String s) {
    Stack<Integer> stack = new Stack<Integer>();
    int max=0;
    int left = -1;
    for(int j=0;j<s.length();j++){
        if(s.charAt(j)=='(') stack.push(j);            
        else {
            //split at j;
            if (stack.isEmpty()) left=j; 
            else{
                stack.pop();
                //valid section
                if(stack.isEmpty()) max=Math.max(max,j-left); 
                //half-valid.
                else max=Math.max(max,j-stack.peek());
               }
        }
    }
    return max;
  }

}

```
#### Reference:
[String methods](http://blog.csdn.net/az44yao/article/details/7582580)
---

