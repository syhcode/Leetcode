## Q70[Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) 

### Solution 1 Recursive
#### Idea:
Normal recursive way.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int climbStairs(int n) {
        return getWay(n,0);
    }
    int getWay(int remained, int way){
        if(remained==0) return way+1;
        if(remained==-1) return way;
        return getWay(remained-2,way)+getWay(remained-1,way);
    }
}
```
### Solution 2 DP
#### Idea:
Use a[] to approach result dynamically.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int climbStairs(int n) {
      if(n<=1) return 1;
      int[] a={1,2};
      for(int i=2;i<n;i++){
          int tmp=a[1];
          a[1]=a[0]+tmp;
          a[0]=tmp;
      }
      return a[1];
    }
}
```
#### Reference:

---

