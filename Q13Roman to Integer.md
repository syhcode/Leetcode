## Q13[Roman to Integer](https://leetcode.com/problems/roman-to-integer/) 

### Solution 1 Hashmap
#### Idea:
If a roman number is smaller than its later number, its sign is'+', or the sign is'-'.Sum all value of roman
numbers showing in the string.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public int romanToInt(String s) {
    HashMap<Character, Integer> map = new HashMap<>();
    map.put('I', 1);
    map.put('V', 5);
    map.put('X', 10);
    map.put('L', 50);
    map.put('C', 100);
    map.put('D', 500);
    map.put('M', 1000);
    int len = s.length();
    int index = 0, result = 0;
    while (index < len) {
        Character chCur = s.charAt(index);
        Character chNext = null;
        if (index + 1 < len)
            chNext = s.charAt(index + 1);
        if(chNext != null && map.get(chCur) < map.get(chNext))
            result -= map.get(chCur);
        else
            result += map.get(chCur);
        index++;
    }
    return result;
  }
}
```
#### Reference:

---

