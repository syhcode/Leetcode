## Q216 [Combination Sum III ](https://leetcode.com/problems/combination-sum-iii/) 

### Solution 1 BackTracking
#### Idea: 
The same as Q78 BackTracking idea 2,but add lines of conditions for the solution.
#### Time Complexity:
O(1)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        int[] nums={1,2,3,4,5,6,7,8,9};
        int sum=0;
    List<List<Integer>> list =new ArrayList<List<Integer>>();
    List<Integer> lists= new ArrayList<Integer>();
    backTrack(0,list,lists,nums,k,n,sum);
    return list;

    }


     public void backTrack(int begin, List<List<Integer>> list, List<Integer> lists,int[] nums,int k,int n,int sum){
        
        List<Integer> newlists= new ArrayList<Integer>();
        for(int i=0;i<lists.size();i++){
          sum=lists.get(i)+sum;
          newlists.add(lists.get(i));
        }
        if(sum==n&&lists.size()==k)  //the condition of the solution
        list.add(newlists);
        
        for (int i = begin; i != nums.length; i++) {

                      lists.add(nums[i]); 

                      backTrack(i+1, list, lists,nums,k,n,0); 

                      lists.remove(lists.size()-1); 


        }
    }
}

```
#### Reference:

---

