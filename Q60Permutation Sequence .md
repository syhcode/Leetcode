## Q60[Permutation Sequence](https://leetcode.com/problems/permutation-sequence/) 

### Solution 1 Recursive
#### Idea:
For the in-order Permutation Sequence,when a prefix or sub-prefix at i change, (i-1)! amount sequences pass.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    String s="";
    ArrayList<Integer> tmp=new ArrayList<Integer>();
    public String getPermutation(int n, int k) {
        if(n==1) return s+1;
        for(int i=1;i<=n;i++) tmp.add(i);
        helper(n,tmp,k-1);
        return s;
    }
    void helper(int len,ArrayList<Integer> tmp,int k ){
         if(len<1) return;
         int[] series={0,1,1,2,6,24,120,720,5040,40320};  
         int pos=k/series[len];
         s=s+tmp.get(pos);
         tmp.remove(pos);
         helper(len-1,tmp,k%series[len]);
    }
}
```
#### Reference:
---

