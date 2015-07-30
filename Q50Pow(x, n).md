## Q50[Pow(x, n)](https://leetcode.com/problems/powx-n/) 

### Solution 1 Divide and Conquer
#### Idea:
In each recursion , the power n divide in half, and result is multiplication of two part and considering a rear.
#### Time Complexity: 
O(logn)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public double myPow(double x, int n) {
      if(n==0) return 1;
      double cur=myPow(x,n/2);
      if(n%2==0) return cur*cur;
      else if(n>0) return x*cur*cur;
      else return cur*cur/x;
    }
}
```
#### Reference:

---

