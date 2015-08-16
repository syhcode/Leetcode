## Q7[Reverse Integer](https://leetcode.com/problems/reverse-integer/) 

### Solution 1 
#### Idea:
Depend on long type to avoid overflow.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int reverse(int x) {
       long sign=1;
       if(x<0){
           x=-x;
           sign=-1;
       }
       long res=0;
       while(x!=0){
           res=x%10+res*10;
           x=x/10;
       }
       res=sign*res;
       if(res>Integer.MAX_VALUE||res<Integer.MIN_VALUE) return 0;
       else return (int)res;
    }
}
```
#### Reference:
---

