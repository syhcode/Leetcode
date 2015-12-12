## Q88 [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) 

### Solution 1
#### Idea:
Cases analyze, when a element in A or B merge in the rear of A,  the processing index of array A or B -1.
#### Time Complexity:
O(m+n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void merge(int A[], int m, int B[], int n) {
     while(m>0 && n>0)
     A[m+n-1]=A[m-1]>B[n-1]?A[--m]:B[--n];
     while(n>0)
     A[n-m-1]=B[--n];
    }
}

```
#### Reference:

---

