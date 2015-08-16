## Q238[Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) 

### Solution 1 
#### Idea:
Consider 0 in array.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] res = new int[nums.length] ;
        int zero=-1; //initiate no zero in array
        int total=1;
        for (int i=0;i<nums.length;i++){
           if(nums[i]==0){
               if(zero==-1){ 
               zero=i;   //only one zero in array
               continue;
               }
               else { 
                   zero=-2;  //more than one zero in array.
                   break;
               }
            }
        total*=nums[i];
        }
        for(int j=0;j<nums.length;j++){
            if(zero==-1) res[j]=total/nums[j];
            else if(zero==-2) res[j]=0;
            else{
                if(j==zero)
                res[j]=total;
                else res[j]=0;
            }
        }
        return res;
    }
}
```
#### Reference:
---

