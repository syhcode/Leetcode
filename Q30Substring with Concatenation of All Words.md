## Q30[Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

### Solution 1 Hashmap
#### Idea:
Deal with also begin with every word.length characters each time, 
Similar with Q76,just use hashmap to identify word instead of character,and this time
the word should appear in order in search string.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<Integer> findSubstring(String S, String[] L) {
        List<Integer> res = new LinkedList<>();
        if (L.length == 0 || S.length() < L.length * L[0].length()) 
           return res;
        int N = S.length(), M = L.length, K = L[0].length();
        Map<String, Integer> map = new HashMap<>();
        Map<String, Integer> curMap = new HashMap<>();
        for (String s : L) {
            if (map.containsKey(s)) 
                map.put(s, map.get(s) + 1);
            else
                map.put(s, 1);
        }
        String str = null, tmp = null;
        for (int i = 0; i < K; i++) {
            // remark: reset count
            int count = 0;   
            
            //l(left):substring head pointer ,r(right) :sweep pointer.
            for (int l = i, r = i; r + K <= N; r += K) {
                str = S.substring(r, r + K);
                if (map.containsKey(str)) {
                    if (curMap.containsKey(str))  
                       curMap.put(str, curMap.get(str) + 1);
                    else  curMap.put(str, 1);

                    if (curMap.get(str) <= map.get(str))    count++;
                    while (curMap.get(str) > map.get(str)) {
                        tmp = S.substring(l, l + K);
                        curMap.put(tmp, curMap.get(tmp) - 1);
                        l += K;
                        if (curMap.get(tmp) < map.get(tmp)) count--;
                    }
                    if (count == M) {
                        res.add(l);
                        tmp = S.substring(l, l + K);
                        curMap.put(tmp, curMap.get(tmp) - 1);
                        l += K;
                        count--;
                    }
                }else {
        
         // the former elements not comply substring condition
                    curMap.clear();
                    count = 0;
                    l = r + K;
                }
            }
          // begin with a new group of search string.
            curMap.clear();
        }
        return res;
    }
}

#### Reference:

---

