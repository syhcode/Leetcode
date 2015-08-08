## Q239[Sliding Window Maximum ](https://leetcode.com/problems/sliding-window-maximum/) 

### Solution 1 Priority Queue
#### Idea:
Using a Descending Priority Queue length of k, and its peek is current window's max val.
#### Time Complexity: 
O(n1ogk) logk is time for queue.remvoe
#### Space Complexity:
O(k)
#### Source code:
```
public class Solution {
   public int[] maxSlidingWindow(int[] nums, int k) {
     int len = nums.length;
     int[] result = new int[len - k + 1];
     if(nums.length == 0) return new int[0];
     Queue<Integer> queue = new PriorityQueue<Integer>(new Comparator<Integer>(){
        public int compare(Integer i1, Integer i2){
            return Integer.compare(i2, i1); // in descending order
        }
     });
     for(int i = 0; i < k; i ++) queue.add(nums[i]);
     result[0] = queue.peek();
     for(int i = k; i < len; i ++){
         queue.remove(nums[i - k]);
         queue.add(nums[i]);
         result[i - k + 1] = queue.peek();
     }
    return result;
   }   
}
```
#### Reference:
---

