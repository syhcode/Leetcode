## Q44[Wildcard Matching](https://leetcode.com/problems/wildcard-matching/) 

### Solution 1 
#### Idea:
Since ? or * can be any value, use two pointers for each string, when pattern has a *, mark it's position, when the later not match,back to
this position next and begin another match process with another one character index difference.
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isMatch(String s, String p) {
        int sIdx = 0, pIdx = 0, cur = 0, starIdx = -1;            
        while (sIdx < s.length()){
            if (pIdx < p.length() && (p.charAt(pIdx) == '?' || s.charAt(sIdx) == p.charAt(pIdx))){
                sIdx++;
                pIdx++;
            }
            // when find p, p move next and mark s and p position.
            else if (pIdx < p.length() && p.charAt(pIdx) == '*'){
                starIdx = pIdx;
                cur = sIdx;
                pIdx++;
            }
           // when diffrent and * exist, pointers of p,s go back to * next
           // * duplicate s from cur to cur + 1,and s next start match:
           // pIdx and sIdx have another one character index difference.
            else if (starIdx != -1){
                pIdx = starIdx + 1;
                cur++;
                sIdx=cur;//eg: a*cck and accck
            }
           //when different or not match, no * exist before
            else return false;
        }
        //rear * judge
        while(pIdx < p.length() && p.charAt(pIdx) == '*')  pIdx++;
        return pIdx == p.length();

    }
}
```
#### Reference:

---

