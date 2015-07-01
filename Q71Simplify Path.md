## Q71[Simplify Path ](https://leetcode.com/problems/simplify-path/) 

### Solution 1 
#### Idea:
Push path in stack skipping the" .. "," . "," ", and when meet ".." pop the former element if (!isEmpty).
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public String simplifyPath(String path) {
    Deque<String> stack = new ArrayDeque<>();
    Set<String> skip = new HashSet<>(Arrays.asList("..",".",""));
    for (String dir : path.split("/")) {
    
    //pop or push method suggest the Deque is used for as a stack.
        if (dir.equals("..") && !stack.isEmpty()) stack.pop();
        if (!skip.contains(dir)) stack.push(dir);
    }
    String res = "";
    for (String dir : stack) res = "/" + dir + res;   //pay attention to iterator order.
    return res.isEmpty() ? "/" : res;
  }

}
```
#### Reference:
[HashSet](http://blog.csdn.net/chindroid/article/details/7741739),
[iterator question](http://stackoverflow.com/questions/16992758/is-there-a-bug-in-java-util-stacks-iterator)
---

