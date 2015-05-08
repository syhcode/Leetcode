## Q33 [Search in Rotated Sorted Array ](https://leetcode.com/problems/search-in-rotated-sorted-array/) 

### Solution 1: binary search in 3 situation
#### Idea: 
considering the three cases for rotated array,and search in each situation recursively.

#### Time Complexity:
O(K^2)
#### Space Complexity:
O(K)
#### Source code:
```
public class Solution {  
    public int search(int[] A, int target) {  
        int len = A.length;  
        if (len == 0) return -1;  
        return binarySearch(A, 0, len-1, target);  
    }  
      
    public int binarySearch(int[] A, int left, int right, int target) {  
       if (left > right) return -1;  
          
       int mid = (left + right) / 2;  
        if (A[left] == target) return left;  
        if (A[mid] == target) return mid;  
       if (A[right] == target) return right;  
         
        //situation 1 :  
        
        
        if (A[left] < A[right]) {   
            if (target < A[left] || target > A[right]) {    //target not exist 
              return -1;  
            } else if (target < A[mid]) {                   //target in left branch  
               return binarySearch(A, left+1, mid-1, target);  
           } else {                                        //target in right branch
                return binarySearch(A, mid+1, right-1, target);  
            }  
       }   
        //situation 2 : 
        else if (A[left] < A[mid]) {   
            if (target > A[left] && target < A[mid]) {      //target in left branch  
               return binarySearch(A, left+1, mid-1, target);  
          } else {                                        //target in right branch  
               return binarySearch(A, mid+1, right-1, target);  
           }  
        }   
        //situation 3
       else {   //A[left]>A[mid]
            if (target > A[mid] && target < A[right]) {     //target in right branch 
               return binarySearch(A, mid+1, right-1, target);  
            } else{                                         //targetin left branch.
                return binarySearch(A, left+1, mid-1, target);  
           }  
        }  
    }  
}  

```
#### Reference:

---

