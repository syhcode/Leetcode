## Q283 [ Move Zeroes](https://leetcode.com/problems/move-zeroes/) 

### Solution 1 two pointer
#### Idea:
two pointer search & mark for nearest positive index(pnum) and zero index(pzero),if pzero<pnum: swap the value, or pnum++; 
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void moveZeroes(int[] nums) {
        int pnum=0;
        int pzero=0;
        int temp = 0;
        while(pzero<nums.length && pnum<nums.length){
            while(pnum<nums.length && nums[pnum]==0 ) pnum++;
          
            while(pzero<nums.length && nums[pzero]!=0 ) pzero++;
               
            if(pnum<nums.length && pzero<nums.length && pzero<pnum){
                nums[pzero] = nums[pnum];
                nums[pnum]=0;
            }
            else{
                pnum++;
            }
        }
    }
}

```
#### Reference:

---

