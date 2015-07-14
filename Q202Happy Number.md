## Q202[Happy Number](https://leetcode.com/problems/happy-number/) 

### Solution 1 HashMap,Recursive
#### Idea:
Normal rear recursive method.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    HashMap<Integer,Integer> map=new HashMap<Integer,Integer>();
    public boolean isHappy(int n) {
        int sum=0;
        while(n!=0){
            sum=sum+(int)Math.pow(n%10,2);
            n=n/10;
        }
        if(map.containsKey(sum)) return false;
        if(sum!=1){
            map.put(sum,0);
            return isHappy(sum);
        }
        else return true;
    }
}
```
#### Reference:

---

