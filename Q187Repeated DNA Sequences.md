## Q187[Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/) 

### Solution 1 Hashmap,Bit manipulation
#### Idea:
Get 10-digits substring one by one, make it into integer code(bit manipulation) to judge the duplication.
Detailedly,As checking the duplicate element, if it was not found before, store the element into the numSet. 
If it was found, store the substring to strSet. When output the result, just use the strSet to get result.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
        public List<String> findRepeatedDnaSequences(String s) {
            List<String> res = new ArrayList<String>();
            HashSet<String> strSet = new HashSet<String>();
            HashSet<Integer> numSet = new HashSet<Integer>();
            for(int i=0; i<s.length() - 9; i++) {

                String substr = s.substring(i, i + 10);
                int curNum = encode(substr);
                if(!numSet.contains(curNum)) {
                    numSet.add(curNum);
                } else {
                    strSet.add(substr);
                }
            }
            for(String str : strSet) {
                res.add(str);
            }
            return res;
        }
   
   //Use bit manipulation to identify the string and help find duplication more easily.
        public int encode(String s) {
            int sum = 0;
            for(int i=0; i<s.length(); i++) {
                if(s.charAt(i) == 'A') {
                    sum *= 4;
                } else if(s.charAt(i) == 'C') {
                    sum = sum * 4 + 1;
                } else if(s.charAt(i) == 'G') {
                    sum = sum * 4 + 2;
                } else if(s.charAt(i) == 'T') {
                    sum = sum * 4 + 3;
                }
            }
            return sum;
        }
    }

```
#### Reference:

---

