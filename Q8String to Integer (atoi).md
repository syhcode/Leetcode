## Q8[String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/) 

### Solution 1
#### Idea:
Cases analysis as notes.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public int myAtoi(String str) {
    int index = 0, sign = 1, total = 0;
    // Empty string
    if(str.length() == 0) return 0;

    // Remove Spaces
    while(index<str.length()&&str.charAt(index) == ' ' )
        index ++;

    // Handle signs
    if(index<str.length()&&(str.charAt(index) == '+' || str.charAt(index) == '-')){
        sign = str.charAt(index) == '+' ? 1 : -1;
        index ++;
    }

    // Convert number and avoid overflow
    while(index < str.length()){
        int digit = str.charAt(index) - '0';
        
        //once'+'or'-' appear, next must be a number, if other character return former formed number;
        //eg "  -0012a42" should return -12,"+-12" return 0;
        if(digit < 0 || digit > 9) break;
        
        //check if total will be overflow after 10 times
        if(Integer.MAX_VALUE/10 < total || Integer.MAX_VALUE/10 == total && Integer.MAX_VALUE %10 < digit)
            return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;

        total = 10 * total + digit;
        index ++;
    }
    return total * sign;
  }
}
```
#### Reference:

---

