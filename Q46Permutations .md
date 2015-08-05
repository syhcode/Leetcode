## Q46[Permutations ](https://leetcode.com/problems/permutations/) 

### Solution 1 Backtrack
#### Idea:
When backtrack remained elements should pick one that DOES'T exist in lists.
#### Time Complexity: 
O(n!)
#### Space Complexity:
O(n!)
#### Source code:
```
public class Solution {
    List<List<Integer>> list=new ArrayList<List<Integer>>();
    List<Integer> lists =new ArrayList<Integer>();
    public List<List<Integer>> permute(int[] nums) {
        ArrayList<Integer> tmp=new ArrayList<Integer>();
        for(int n:nums) tmp.add(n);
        backtrack(tmp);
        return list;
    }
    void backtrack(ArrayList<Integer> tmp){
        if(tmp.size()==0){
            list.add(new ArrayList<Integer>(lists));
            return;
        }
       for(int i=0;i<tmp.size();i++){
            int ele=tmp.get(i);
            lists.add(ele);
            tmp.remove(i);
            backtrack(tmp);
            tmp.add(i,ele);
            lists.remove(lists.size()-1);
       }
    }
}
```
#### Reference:
---

