## Q55 [Jump Game](https://leetcode.com/problems/jump-game/) 

### Solution 1 Greedy
#### Idea:
from the first position,greedily update the accessible position by each element until it can not move forward (meet 0),namely fail,or
it will access to the end by assuming each element can move one position at least.


#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean canJump(int[] nums) {
       

    int len=nums.length;
    int access=nums[0];
    for(int i=1;i<len;i++)
    {
        if(access<i)//cannot jump forward in current position;
        return false;
       
       //update the further position can access
        access=access>i+nums[i]?access:i+nums[i]; 
    }
   
    return true;
    }
}

```
#### Reference:

---

