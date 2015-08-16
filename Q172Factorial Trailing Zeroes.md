## Q172[Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/) 

### Solution 1 
#### Idea:
Count factor of 5 in n, n-1, ...2,1 .
#### Time Complexity: 
O(log5(n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int trailingZeroes(int n) {
        int count=0;
        long tmp=5;
        while(tmp<=n){
            count+=n/tmp;
            tmp*=5;
        }
        return count;
    }
}
```
#### Reference:
---

