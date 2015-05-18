## Q62 [Unique Paths](https://leetcode.com/problems/unique-paths/) 

### Solution 1 Combination a/b
#### Idea:
The robot has m-1 times to move down,and n-1 times to move right,so the sum of paths are Cm-1/m+n-2 or Cn-1/m+n-2.Also while calculating ,long type can avoid overflow.
#### Time Complexity:
O(min(m,n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int uniquePaths(int m, int n) {
        int temp;
        int N=m-1+n-1;
        if(m>n){
            temp=m;
            m=n;
            n=temp;
            
        }
      long sum=1;
        for(int i=1;i<=m-1;i++){
            sum=sum*(N+1-i)/i;
            
        }
        return (int)sum;
    }
}

```
#### Reference:

---

### Solution 2 DP
#### Idea:
each step has two ways to reach, its left or its up, and the sum of ways to this step equals sum of ways to its left or its right.
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(m*n)
#### Source code:
```
public class Solution {
    public int uniquePaths(int m, int n) {
       int[][] path=new int [m][n];
       
       for(int i=0;i<m;i++)
       path[i][0]=1;
       for(int i=0;i<n;i++)
       path[0][i]=1;
       
       for(int i=1;i<m;i++){
           for(int j=1;j<n;j++){
              path[i][j]=path[i-1][j]+path[i][j-1]; 
               
           }
       }
  
  
  return path[m-1][n-1];
  
    }
}
```
#### Reference:

---