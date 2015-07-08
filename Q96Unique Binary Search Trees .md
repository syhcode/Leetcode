## Q96[Unique Binary Search Trees ](https://leetcode.com/problems/unique-binary-search-trees/) 

### Solution 1 DP
#### Idea:
Math DP method.f(n) is related to f(0)~f(n-1).
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int numTrees(int n) {
        if(n==0) return 1;
		else if(n==1) return 1;
		else if(n==2) return 2;
		else{
		    int res=0;
			for(int i=1;i<=n/2;i++)
			res=res+numTrees(n-i)*numTrees(i-1);
			if(n%2==1) res=res*2+numTrees(n/2)*numTrees(n/2);
			else res=res*2;
			return res;
		}
    }
}
```
#### Reference:

---

