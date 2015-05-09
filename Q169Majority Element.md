## Q169 [Majority Element](https://leetcode.com/problems/majority-element/) 

### Solution 1
#### Idea:
Since majority element ALWAYS exists,utilize Moore voting algorithm.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
 public int majorityElement(int[] nums) {
    int temp = nums[0];
    int count = 0;
    for(int n : nums) {
        if(n == temp) {
            count++;
        }
        else {
            count--;
        }
        if(count == 0) { 
            temp = n;
            count = 1;
        }
    }
    return temp;
 }
}

```
#### Reference:

---
### Solution 2 HashMap
#### Idea:
HashMap is an effective to avoid duplicated elements in collection.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int majorityElement(int[] nums) {
        
   
        Map<Integer,Integer> hash = new HashMap<Integer,Integer>();
            for (int key: nums)
                if (!hash.containsKey(key))
                    hash.put(key,0);
                else
                    hash.put(key,hash.get(key)+1);
            for (Map.Entry<Integer,Integer> entry: hash.entrySet())
                if (entry.getValue() >= nums.length/2)
                   
                    return entry.getKey();
            return 0;


        
    }
}

```
#### Reference:

---


