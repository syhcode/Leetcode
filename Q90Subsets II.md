## Q90 [Subsets II](https://leetcode.com/problems/subsets-ii/) 
 
 
### Solution 1 BackTracking
#### Idea:
Idea is the same as Q78 Subsets, but in order to avoid the duplicated subsets, the method is to make all the  same elements
only appear only ONCE AT the time they are built.(in order to think it through, just assume that the subsets are built from size=1~n,and the elements fill in by order.  )
#### Time Complexity:
O(2^n)
#### Space Complexity:
O(2^n)
#### Source code:
```

public class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        
    Arrays.sort(nums);
    List<List<Integer>> list =new ArrayList<List<Integer>>();
    List<Integer> lists= new ArrayList<Integer>();
    backTrack(0,list,lists,nums);
    return list;
 
 }


     public void backTrack(int begin, List<List<Integer>> list, List<Integer> lists,int[] nums){
        
      
        List<Integer> newlists= new ArrayList<Integer>();
        for(int i=0;i<lists.size();i++)
        newlists.add(lists.get(i));
        list.add(newlists);
       
       	for (int i = begin; i <nums.length; ++i) {
       	
       	  // make all the  same elements only appear only once at the time they are built.
       	  
       	    if (i!=begin && nums[i] == nums[i-1]) continue;
					
			          lists.add(nums[i]); 
			          
			        //attempt new way or solution 
			          backTrack(i+1, list, lists,nums); 
			          
//when the next loop process finish, namely have sweep all the possible solution collections,
//ignore the solution and continue the current loop;

			          lists.remove(lists.size()-1); 
			          
			          
       	}
    
        
        
    }
}
```

#### Reference:

---

