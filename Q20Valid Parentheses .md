## Q20[Valid Parentheses  ](https://leetcode.com/problems/valid-parentheses/) 

### Solution 1 Stack
#### Idea:
Store the appearance situation of correspond character of a character in STACK, and judge if they appear in pair.  
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public boolean isValid(String s) {
    char[] chars = s.toCharArray();
    Map<Character,Character> pairs = new HashMap<Character,Character>();
    pairs.put('(', ')');
    pairs.put('{', '}');
    pairs.put('[', ']');

    Stack<Character> stack = new Stack<Character>();
     
    for (char tmp:chars) {
        if (pairs.containsKey(tmp)) {
            stack.push(pairs.get(tmp));
        } else {
            if (stack.isEmpty() || tmp != stack.pop()) return false;
        }
    }
    return stack.isEmpty();
  }

}
```
#### Reference:

---

