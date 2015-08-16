## Q241[Different Ways to Add Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/) 

### Solution 1 Div & Conq
#### Idea:
Split the string by each operator,for every two split part get their possible result respectively,then combine these results.
If input is a single number without operator,the result is this number.
#### Time Complexity: 
O(n+m)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<Integer> diffWaysToCompute(String input) {
        List<Integer> res = new LinkedList<Integer>();
        for (int i=0; i<input.length(); i++) {
            if (input.charAt(i) == '-' 
                   ||input.charAt(i) == '*' ||input.charAt(i) == '+' ) {                
                String part1 = input.substring(0, i);
                String part2 = input.substring(i+1);
                List<Integer> res1 = diffWaysToCompute(part1);
                List<Integer> res2 = diffWaysToCompute(part2);
                for (Integer p1 :   res1) {
                    for (Integer p2 :   res2) {
                        int c = 0;
                        switch (input.charAt(i)) {
                            case '+': c = p1+p2;
                                break;
                            case '-': c = p1-p2;	
                                break;
                            case '*': c = p1*p2;
                                break;
                        }
                        res.add(c);
                    }
                }
            }
        }
        //input is only one number,no operator thus can not mathch if() to add number.
        if (res.size() == 0) { 
            res.add(Integer.valueOf(input));
        }
        return res;
    }
}

```
#### Reference:
---

