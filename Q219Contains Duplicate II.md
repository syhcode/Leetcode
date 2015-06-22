## Q219[Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/) 

### Solution Hashmap
#### Idea:
Build map<nums[i],i>,judge the duplicated element's distance, if(distance>k) update the 'i' in the map.  
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
      Map<Integer,Integer> map=new HashMap<Integer,Integer>();
      for(int i=0;i<nums.length;i++){
         if(!map.containsKey(nums[i]))
         map.put(nums[i],i);
         else{
             int dis=i-map.get(nums[i]);
             if (dis<=k)
             return true;
             else map.put(nums[i],i);
         }
       }
            return false;
    }
}
```
#### Reference:

---

