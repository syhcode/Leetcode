## Q229[Majority Element II](https://leetcode.com/problems/majority-element-ii/) 

### Solution 1 Moore voting Algorithms
#### Idea:
Imply Moore voting Algorithms in two turns, and we get most two majority elements, then we calculate their 
appearing times and add to the list. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<Integer> majorityElement(int[] nums) {
    List<Integer> res=new ArrayList<Integer>();
    if(nums.length == 0) return res;
    int turn1 = -1, turn2 = -1, count1 = 0, count2 = 0;
    for(int num : nums){
        if(num == turn1) count1++;
        else if(num == turn2) count2++;
        else if (count1 == 0) {turn1 = num; count1++;}
        else if (count2 == 0) {turn2 = num; count2++;}
        else {
            count1--;
            count2--;
        }
    }
    count1 = 0; count2 = 0;
    for(int num : nums){
        if(num == turn1) count1 += 1;
        if(num == turn2) count2 += 1;
    }
    if(count1 > nums.length/3) res.add(turn1);
    if(count2 > nums.length/3) res.add(turn2);
    return res;
    }
}
```
#### Reference:
---

