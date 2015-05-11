## Q45 [Jump Game II](https://leetcode.com/problems/jump-game-ii/) 

### Solution 1 Greedy
#### Idea:
from the first position,greedily update the accessible position by each element,then, we can define the access area collection as the graph,
from the graph, before reach the goal, we can just count the right edge of each access area and get the min step to the goal.
The graph as: ![](https://github.com/syhcode/Leetcode/blob/master/image/Q45.png)

#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int jump(int[] nums) {
   
    int len=nums.length;
    int pre_access=0;
    int access=0;
    int count=0;
    for(int i=0;i<len-1&&pre_access<nums.length-1;i++)
    {
      
        if(access<i+nums[i]){
        access=i+nums[i]; 
        }
        if(i==pre_access){
            count++;
            pre_access=access;
        }
     }
     
     return count;
    }
}

```
#### Reference:

---

