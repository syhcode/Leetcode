## Q66 [Plus One](https://leetcode.com/problems/plus-one/) 

### Solution 1
#### Idea:
Pay attention to that if final cout=1,should build a new array.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1) or O(n)
#### Source code:
```
public class Solution {
    public int[] plusOne(int[] digits) {
        int cout=1;
        int len=digits.length;
        for (int i=len-1;i>=0;i--){
           
            digits[i]=digits[i]+cout;
            if (digits[i]>9) {digits[i]=digits[i]-10;cout=1;}
            else cout=0;
         
        }
            if (cout==1){
                int[] plus=new int[len+1];
                plus[0]=1;
                return plus;
                
            }
                
             return digits;
        
    }
        
}

```
#### Reference:

---

