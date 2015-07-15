## Q6[ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/) 

### Solution 1 
#### Idea:
Each time deal with a line of string.The "key" suggest a group of zigzag amount. For each row there is a math
pattern about "key" for elements in row mapping the position in the string.
#### Time Complexity: 
O(n*m)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public String convert(String s, int numRows) {
        int key=numRows<2?numRows:2*numRows-2;
        StringBuilder res = new StringBuilder();
        
        for(int i=0;i<=numRows-1;i++){
            for(int j=0;j<s.length();j++){
                if(i==0||j==numRows-1){
                    if((j-i)%key==0)
                    res.append(s.charAt(j));
                }
                else{  //the down column;
                    if(j%key<=numRows-1){
                        if((j-i)%key==0){
                            res.append(s.charAt(j));
                        }
                    }
                    else{ // the up column;
                        if((j+i)%key==0){
                            res.append(s.charAt(j));
                        }
                    }
                }
            }
        }
        return res.toString();
    }
}
```
#### Reference:

---

