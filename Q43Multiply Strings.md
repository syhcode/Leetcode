## Q43[Multiply Strings](https://leetcode.com/problems/multiply-strings/) 

### Solution 1
#### Idea:
Store digit*digit result(double digit or single digit) in corresponding position in the array.
Then process the carry and digit.
#### Time Complexity: 
O(m*n)
#### Space Complexity:
O(m+n)
#### Source code:
```
public class Solution {
    public String multiply(String num1, String num2) {
        if(num1.length()==0||num2.length()==0) return "";
        if(num1.equals("0")||num2.equals("0")) return "0";
        int n1 = num1.length(), n2 = num2.length();
        int[] products = new int[n1 + n2];
        for (int i = n1 - 1; i >= 0; i--) {
            for (int j = n2 - 1; j >= 0; j--) {
                int d1 = num1.charAt(i) - '0';
                int d2 = num2.charAt(j) - '0';
                products[i + j + 1] += d1 * d2;
            }
        }
        int carry = 0;
        for (int i = products.length - 1; i >= 0; i--) {
            int tmp = (products[i] + carry) % 10;
            carry = (products[i] + carry) / 10;
            products[i] = tmp;
        }
        StringBuilder sb = new StringBuilder();
        for (int num : products) sb.append(num);
        
//when a number's length != another one,the product length may = n1+n2-1,thus head is'0'.
        if (sb.charAt(0) == '0') sb.deleteCharAt(0);
        return  sb.toString();
    }
}

```
#### Reference:
[String methods](http://blog.csdn.net/az44yao/article/details/7582580)
---

