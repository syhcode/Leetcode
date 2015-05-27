## Q31 [Next Permutation](https://leetcode.com/problems/next-permutation/) 

### Solution 1 
#### Idea:
(1)Begin from the end of array, find the ele[i]>ele[i-1]; (2)From array i to len-1, find ele[k]>ele[i-1]; (3) Swap ele[k] and ele[i-1]; (4) Reverse array from i to len-1.
 
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void nextPermutation(int[] nums) {
        int len=nums.length;
        int temp;
        for(int i=len-1;i>0;i--){
					    
		   if(nums[i]>nums[i-1]){  //step (1)
				    	
				    	for(int k=len-1;k>=i;k--){ // step (2), step(3)
				    		if(nums[k]>nums[i-1]){
				    		temp=nums[k];
					        nums[k]=nums[i-1];
					        nums[i-1]=temp;
					        break;
					        }
				    	      
				    	 }
				           for (int j=0;j<(len-i)/2;j++){  //step(4)
				               temp=nums[i+j];
				               nums[i+j]=nums[len-1-j];
				               nums[len-1-j]=temp;
				           }
				          break;
			}
				       
			     if(i==1)   // if no solution,reverse all array.
				   for (int j=0;j<len/2;j++){
				   temp=nums[j];
				   nums[j]=nums[len-1-j];
				   nums[len-1-j]=temp;
				   }
				       
				
	    }
				
    }
}

```
#### Reference:

---

