## Q11 [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) 

### Solution 1
#### Idea:
Initialize case that two endpoints are with max X, then find bigger hight and compare with the former area, get the larger area.

#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int maxArea(int[] height) {
      
       int i=0;
       int j=height.length-1;
       int temp;
       int maxArea=0;
       while(i<j)
       {   
           temp=(j-i)*(height[i]<=height[j]?height[i]:height[j]);
           
           maxArea= maxArea>=temp?maxArea:temp;
          
    
           if(height[i]<=height[j]) i++;
           
           else j--;
           
       }
       

       return maxArea;
        
    }
}

```
#### Reference:

---

