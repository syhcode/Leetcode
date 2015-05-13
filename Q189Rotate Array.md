## Q189 [Rotate Array ](https://leetcode.com/problems/rotate-array/) 

### Solution 1 Recursive
#### Idea:
In recursive process,roughly len/2>k or len/2<k, cases are divided into two situations,and then from the start position of two parts, swap the elements as much as we can,then update the parameter in function swap().


#### Time Complexity:
O(n), the worst case for iteration times:k=1 or k=nums.length-1
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {

    public void rotate(int[] nums, int k) { 
        
         boolean result=false;
          int len=nums.length;
          
	      if (len<k) k=k%len;
		  if(k>0)
	      swap(nums,k,0,result);
        
    }
        

  private void swap(int[] nums,int k, int start,boolean result){
	      
	      int temp;
	      int len=nums.length;
	if(k>=1&&len>k&& result==false){
	         
	     //situation 1:k<¡÷len/2 
	     
	  if((len-start-k)-k>=0 ){ 
	      
	      if(len-start-k-k==0||k==0) result=true;
	      
	        for(int i=0;i<k;i++){
	        
	          temp=nums[i+start];
	          nums[i+start]=nums[len-k+i];
	          nums[len-k+i]=temp;
	        
	         }
	         
	          swap(nums,k,start+k,result);
	          
	   }
	      //situation 1:k>¡÷len/2
	      
	     if (len-start-k-k<0 ){
	        
	          if(len-start-k-k==0||k==0) result=true;
	          
	          for(int i=0;i<len-start-k;i++){
	          
	              temp=nums[i+start];
	              nums[i+start]=nums[len-k+i];
	              nums[len-k+i]=temp;
	              
	          }
	        swap(nums,k-(len-start-k), len-k,result);
	      }
	     
	    }    
	   
  }
}  

```
#### Reference:

---

