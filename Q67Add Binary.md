## Q67[Add Binary](https://leetcode.com/problems/add-binary/) 

### Solution 1 
#### Idea:
Reducing cases analysis by while(i >= 0 || j >= 0 || carry == 1).
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public String addBinary(String a, String b) {
        if(a == null || a.isEmpty()) 
            return b;
        if(b == null || b.isEmpty()) 
            return a;
        StringBuilder stb = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        int aBit;
        int bBit;
        int carry = 0;
        int result = 0;

        while(i >= 0 || j >= 0 || carry == 1) {
            aBit = (i >= 0) ? a.charAt(i--)-'0' : 0;
            bBit = (j >= 0) ? b.charAt(j--)-'0' : 0;
            result = aBit ^ bBit ^ carry;
            carry = ((aBit + bBit + carry) >= 2) ? 1 : 0;
            stb.append(result);
        }
        return stb.reverse().toString();
    }
}

```
#### Reference:

---

