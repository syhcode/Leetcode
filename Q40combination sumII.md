## Q40 [Combination SumII](https://leetcode.com/problems/combination-sum-ii/) 

### Solution 1 : Recursive
#### Idea: 
1st,like Q39,utilize recursive method, for each circle begin with a number in candidates ,but skip this nunmber while searching
the array sum in target.
2st,delete the annoying duplicated element.

#### Time Complexity:
O(??)
#### Space Complexity:
O(n?)
#### Source code:
```
public class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        getResult(result, new ArrayList<Integer>(), candidates, target, 0);
        dedup(result);   //delete duplicated element
        return result;
    }

    private void getResult(List<List<Integer>> result, List<Integer> cur, int candidates[], int target, int start){      
        if(candidates.length==1){
            if (candidates[0]==target) {cur.add(candidates[0]);result.add(new ArrayList<Integer>(cur));}
        }
        else{
        if(target > 0){
            for(int i = start; i < candidates.length && target >= candidates[i]; i++){
                int  j=i; j++;
                cur.add(candidates[i]);
                getResult(result, cur, candidates, target - candidates[i], j);
                cur.remove(cur.size() - 1);
            }
        }
        else if(target == 0 ){
            result.add(new ArrayList<Integer>(cur));
       }
        }
  
    } 

    private void dedup(List<List<Integer>> result){
        List<Integer> temp=new ArrayList<Integer>();
        for(int i=0;i<result.size();i++){
           temp=result.get(i);
        for(int j=i+1;j<result.size();j++)
           if (temp.equals(result.get(j)))
              {result.remove(j);j--;}
            
        }
    }
    
}

```
#### Reference:

---

