## Q[Combination Sum](https://leetcode.com/problems/combination-sum/) 

### Solution 1 : Recursive
#### Idea: 
utilize recursive method, for each circle begin with a number in candidates,search the array sum in target.
#### Time Complexity:
O(??)
#### Space Complexity:
O(n?)
#### Source code:
```
public class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        getResult(result, new ArrayList<Integer>(), candidates, target, 0);

        return result;
    }

    private void getResult(List<List<Integer>> result, List<Integer> cur, int candidates[], int target, int start){
        if(target > 0){
            for(int i = start; i < candidates.length && target >= candidates[i]; i++){
                cur.add(candidates[i]);
                getResult(result, cur, candidates, target - candidates[i], i);
                cur.remove(cur.size() - 1);
            }
        }
        else if(target == 0 ){
            result.add(new ArrayList<Integer>(cur));
        }
    }
}

```
#### Reference:

---

