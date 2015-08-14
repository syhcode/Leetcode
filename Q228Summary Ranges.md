## Q228[Summary Ranges](https://leetcode.com/problems/summary-ranges/) 

### Solution 1 
#### Idea:
Cases analysis, deal when the current ele != the former ele +1, then finally process the end range.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> list=new ArrayList<String>();
        if(nums.length==0) return list;
        int head= nums[0];
        for(int i=1;i<nums.length;i++){
		   if(nums[i]!=nums[i-1]+1){
			   if(head!=nums[i-1]){
			       String add=head+"->"+nums[i-1];
			       list.add(add);
			       head=nums[i];
			   }else{
			       list.add(new String(""+nums[i-1]));
			       head=nums[i];
			   }
		    }
		}
		//process the end one range
        if(head==nums[nums.length-1])
        list.add(new String(""+head));
        else list.add(new String(head+"->"+nums[nums.length-1]));
        return list;
    }
}
```
#### Reference:
---

