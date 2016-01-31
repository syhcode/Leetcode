## Q319[Bulb Switcher](https://leetcode.com/problems/bulb-switcher/) 

### Solution 1 
#### Idea:
brute force or math.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
/* this problem can be solved by  return (int)Math.sqrt(n):
since all number have even number of factors except square number(9:1,3,9),
we just need to count how many square number smaller than n;
*/
public class Solution {
    public int bulbSwitch(int n) {
        int[] a=new int[n];
        for(int span=1;span<=n;span++)
        for(int i=-1+span;i<n;i+=span){
            a[i]^=1;
        }
        int num=0;
        for(int temp:a){
            if(temp == 1) num++;
        }
        return num;
    }
}

```
#### Reference:

---

