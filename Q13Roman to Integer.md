## Q13[Roman to Integer](https://leetcode.com/problems/roman-to-integer/) 

### Solution 1 Hashmap
#### Idea:
Add current number first, then If this roman number is smaller than its later number,subtract 2 times of it from the sum because it has been added.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int romanToInt(String s) {
        HashMap<Character,Integer> map=new HashMap<Character,Integer>();        		map.put('I',1);map.put('V',5);map.put('X',10);map.put('L',50);map.put('C',100);map.put('D',500);map.put('M',1000);
        char pre=' ';
        int sum=0;
        for(int i=0;i<s.length();i++){
            char c =s.charAt(i);
            sum+=map.get(c);
            if(pre!=' ' && map.get(c)>map.get(pre)) sum=sum-2*map.get(pre);
            pre = c;
        }
        return sum;
    }
}
```
#### Reference:

---

