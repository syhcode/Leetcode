## Q134[Gas Station](https://leetcode.com/problems/gas-station/) 

### Solution 1 
#### Idea:
If sum of gas[]>sum of cost[],there must be a solution. If can travel from station i to j but j+1, then 
no starting station from i to j can reach j+1, thus begin search from station j+1 as a start station.
Moreover, there may not be only one solution.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int begin=0,sum=0,tank=0;
        for(int i=0;i<gas.length;i++){
            tank+=gas[i]-cost[i];
            sum+=gas[i]-cost[i];
            if(tank<0){
                begin=i+1;
                tank=0;
            }
        }
    return sum>=0? begin:-1;    
    }
}
```
#### Reference:
---

