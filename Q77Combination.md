## Q77[Combination](https://leetcode.com/problems/combinations/) 

### Solution 1 Backtrack
#### Idea:
Normal backtrack.
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
public class Solution {
    List<List<Integer>> list=new ArrayList<List<Integer>>();
    List<Integer> lists =new ArrayList<Integer>();
    public List<List<Integer>> combine(int n, int k) {
        ArrayList<Integer> tmp=new ArrayList<Integer>();
        for(int i=1;i<=n;i++) tmp.add(i);
        backtrack(tmp,k,0);
        return list;
    }
    void backtrack(ArrayList<Integer> tmp,int k,int cur){
        if(lists.size()==k){
            list.add(new ArrayList<Integer>(lists));
            return;
        }
       for(int i=cur;i<tmp.size();i++){
            lists.add(tmp.get(i));
            backtrack(tmp,k,i+1);
            lists.remove(lists.size()-1);
       }
    }
}
```
#### Reference:
---

