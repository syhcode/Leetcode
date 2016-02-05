## Q306[ Additive Number](https://leetcode.com/problems/additive-number/) 

### Solution 1 
#### Idea: 
Traverse all the possible first two combinations using two pointers, meanwhile do recursion with remained string.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    // use BigInteger.add(new BigInteger("123123")).toString(), do not overflow.
    public boolean isAdditiveNumber(String num) {
        boolean flag = false;
        for(int i=1;i<=num.length()/2;i++){  
            if(num.charAt(0)=='0' && i>1 ) break;
            for(int j=i+1;j<num.length();j++){
                if(num.charAt(i)=='0' && j>i+1) break;
                Long a= Long.valueOf(num.substring(0,i)); 
                Long b= Long.valueOf(num.substring(i,j)); 
                if (isAddtive(a,b,num.substring(j))) flag = true;  
            }
        }
        return flag;
    }
    boolean isAddtive(Long a, Long b, String remain){
        Long c = a+b;  
        int len = c.toString().length(); 
        String s = c.toString(); 
        if(remain.equals(s)) return true;
        if(!remain.startsWith(s)) return false; // startsWith
        return isAddtive(b,c,remain.substring(len)); 
    }
}

```
#### Reference:

---

