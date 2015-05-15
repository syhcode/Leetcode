## Q78 [Subsets](https://leetcode.com/problems/subsets/) 
 
 
### Solution 1 Bit Manipulation
#### Idea:
There is 2^n existing(0 or 1) status of each element in array[n] corresponding to Subsets, and so we build 2^n existing status models(lists)
to modify the all elements,then we do the process by judging that if a element's position existing satatus is '1' or '0' (move to right end and '&' with 1),
the '1' status suggest it exist in the current model and add it to the list of this model.

#### Time Complexity:
O(n*2^n)
#### Space Complexity:
O(2^n)
#### Source code:
```

public class Solution {
 public List<List<Integer>> subsets(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> result = new ArrayList<List<Integer>>();
    int index = 0;
    int length = nums.length;
    for(int i = 0; i < Math.pow(2, length); i++){  //in total 2^length models
        List<Integer> set = new ArrayList<Integer>();
      
        for(int j = 0; j < length; j++){   // judge if this element exist in current model
            if(((i>>j)&1) != 0){
                set.add(nums[j]);
            }
        }
        result.add(set);
    }
    return result;
 }

}

```
#### Reference:

---

### Solution 2 BackTracking
#### Idea:
in backtracking thought,first we build the sweep area dynamically.  
For nums[n],2 status (exist or not)for each element in subsets,we can sweep the status tree with conditions that the sweep depth is n(nums.length).

#### Time Complexity:
O(2^n)
#### Space Complexity:
O(2^n)
#### Source code:
```

public class Solution {
 public List<List<Integer>> subsets(int[] nums) {
 
    Arrays.sort(nums);
    List<List<Integer>> list =new ArrayList<List<Integer>>();
    List<Integer> lists= new ArrayList<Integer>();
    backTrack(0,list,lists,nums);
    return list;
 
 }


     public void backTrack(int n,List<List<Integer>> list, List<Integer> lists,int[] nums){
        
        int len=nums.length;
    
        if (n==len){
        List<Integer> newlists= new ArrayList<Integer>();
        for(int i=0;i<lists.size();i++)
        newlists.add(lists.get(i));
        list.add(newlists);
       
      
      
     }
        else{
           
           lists.add(nums[n]); 
           
           backTrack(n+1,list,lists,nums);
           lists.remove(lists.size()-1);   
           backTrack(n+1,list,lists,nums);
         
         
            
        }
        
        
    }
    
    
}


```
### In another form:
```
public class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        
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
       
       	for (int i = begin; i != nums.length; ++i) {
					
			          lists.add(nums[i]); 
			         
			          backTrack(i+1, list, lists,nums); //attempt new way or solution
			          
//when the next loop process finish, namely have sweep all the possible solution collections,
//ignore the solution and continue the cuttent loop;

			          lists.remove(lists.size()-1); 
			          
			          
       	}
    
        
        
    }
}
```

#### Reference:

---

