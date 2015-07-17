## Q65[Valid Number](https://leetcode.com/problems/valid-number/) 

### Solution 1 Regular Expression
#### Idea:
Depend on String.matches() method and find the number's pattern.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isNumber(String s) {
    return s.matches("(\\s*)[+-]?((\\.[0-9]+)|([0-9]+(\\.[0-9]*)?))(e[+-]?[0-9]+)?(\\s*)");
    }
}
```
### Solution 2 
#### Idea:
Use flags to mark the appearance of characters, judge these flags. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public boolean isNumber(String s) {
    s = s.trim();

    boolean pointSeen = false;
    boolean eSeen = false;
    boolean numberSeen = false;
    //numAfterE make 'e' between numbers ,or no 'e' situations true
    //its depend on 'e' and number appearance order.
    boolean numberAfterE = true;
    for(int i=0; i<s.length(); i++) {
        if('0' <= s.charAt(i) && s.charAt(i) <= '9') {
            numberSeen = true;
            numberAfterE = true;
        } else if(s.charAt(i) == '.') {
            if(eSeen || pointSeen) {
                return false;
            }
            pointSeen = true;
        } else if(s.charAt(i) == 'e') {
            if(eSeen || !numberSeen) {
                return false;
            }
            //numberAfterE = false;
            eSeen = true;
        } else if(s.charAt(i) == '-' || s.charAt(i) == '+') {
            if(i != 0 && s.charAt(i-1) != 'e') {
                return false;
            }
        } else {
            return false;
        }
    }

    return numberSeen && numberAfterE;
  }
}
```
#### Reference:
[Regular Expression](http://blog.csdn.net/luosijin123/article/details/4792181)
[common RE](http://www.jb51.net/article/34155.htm)
---

