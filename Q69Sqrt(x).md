## Q69[Sqrt(x)](https://leetcode.com/problems/sqrtx/) 

### Solution 1 Binary Search
#### Idea:
Use a+(b-a)/2 instead of(a+b)/2 and use pow(c,d) instead of c^d to compare can avoid overflow.
#### Time Complexity: 
O(logn)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int mySqrt(int x) {
        int left=1,right=x,mid=1;
		while(left<=right){
			mid=left+(right-left)/2;
			if(Math.pow(mid,2)<=x) left=mid+1;
			else right=mid-1;
		}
	return Math.min(left,right);
    }
}

OR:

public class Solution {
    public int mySqrt(int x) {
        if(x<2) return x;
        int left=1,right=x,mid=0;
        while(right>=left){
            mid=(left+right)/2;
            if (mid<=x/mid && (mid+1)>x/(mid+1)) return mid;
            else if (mid>x/mid) right=mid-1;
            else left=mid+1;
        }
        return mid;
    }
}

```
#### Reference:

---

