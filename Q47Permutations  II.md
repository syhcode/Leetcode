## Q47[Permutations II ](https://leetcode.com/problems/permutations-ii/) 

### Solution 1 Backtrack
#### Idea:
Same algorithms with Q46, but sort array first and avoid prefix duplicated number for each different number
while backtracking.
#### Time Complexity: 
O(n!) the worst case
#### Space Complexity:
O(n!)
#### Source code:
```
public class Solution {
    List<List<Integer>> list=new ArrayList<List<Integer>>();
    List<Integer> lists =new ArrayList<Integer>();
    public List<List<Integer>> permuteUnique(int[] nums) {
        Arrays.sort(nums);
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
            while (i+1<tmp.size()&&tmp.get(i+1)==tmp.get(i)) i++;
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

