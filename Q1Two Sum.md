## Q1 [Two Sum](https://leetcode.com/problems/two-sum/) 

### Solution 1 HashMap
#### Idea:
Use Hash map to store the element' <needed_value / my_position>; later sweep based on current element value, when find the needed_value corresponding to any former element,
catch this current position and the former position,otherwise store current element' <needed_value / my_position>.
 
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {

  public int[] twoSum(int[] numbers, int target) {
    int[] result = new int[2];
    Map<Integer, Integer> map= new HashMap<Integer, Integer>();

    for(int i = 0; i < numbers.length; i++){
       
        if(!map.containsKey(numbers[i]))
        map.put(target - numbers[i], i);
        
        else{
        
            result[0] = map.get(numbers[i]) + 1; //former position
            
            result[1] = i + 1;  //current position
        
           map.put(target - numbers[i], i);
        }
    }

    return result;
  }

}


```
#### Reference:

---

