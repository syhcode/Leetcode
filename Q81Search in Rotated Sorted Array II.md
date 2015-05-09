## Q81 [Search in Rotated Sorted Array ](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) 

### Solution 1: binary search in 3 situation
#### Idea: 
Just like Q33,considering the three cases for rotated array,and search in each situation recursively.HOWEVER, when get the same
ele[left],ele[right] or ele[left],ele[mid],wipe out these elements by "right-1" during binary search. 
And the three cases as picture: ![](https://github.com/syhcode/Leetcode/blob/master/image/q33.jpg)
#### Time Complexity:
O(log(n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {  
    public boolean search(int[] A, int target) {  
       
        int len = A.length;  
        if (len == 0) return false;  
        return binarySearch(A, 0, len-1, target);  
    }  

    public boolean binarySearch(int[] A, int left, int right, int target) {  
       if (left > right) return false;  

       int mid = (left + right) / 2;  
       if (A[left] == target) return true;  
       if (A[mid] == target) return true;  
       if (A[right] == target) return true;  

      // skip the duplicated non-value left(head) and right(rear) element while searching.
      
       if(A[left]==A[right]&& A[left]!=target)  return binarySearch(A, left, right-1, target);
      
       if(A[left]==A[mid]&& A[left]!=target)  return binarySearch(A, left, right-1, target);
        
        //situation 1 :  
        
       if (A[left] < A[right]) {   
            if (target < A[left] || target > A[right]) {    //target not exist 
              return false;  
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

       else if (A[left]>A[mid]){  
            if (target > A[mid] && target < A[right]) {     //target in right branch 
               return binarySearch(A, mid+1, right-1, target);  
            } else{                                         //targetin left branch.
                return binarySearch(A, left+1, mid-1, target);  
           }  
        }  
    
        return false;
    }  
}  

```
#### Reference:

---

