## Q217 [Contains Duplicate ](https://leetcode.com/problems/contains-duplicate/) 

### Solution 1 HashMap
#### Idea:  
Build hashmap to store and determine duplication. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        Map<Integer,Integer> hash=new HashMap<Integer,Integer>();
        for(int key: nums){
            if(!hash.containsKey(key))
            hash.put(key,0);
            else return true;
        }
       return false; 
    }
}
```
#### Reference:

---

