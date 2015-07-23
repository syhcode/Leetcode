## Q91[Decode Ways](https://leetcode.com/problems/decode-ways/) 

### Solution 1 DP
#### Idea:
The s[0~n] decode ways can be defined by s[0~n-1] decode ways (sub1)and s[0~n-2] decode ways(sub2).
If s[n] can pair with s[n-1], s[0~n] decode ways= sub1+sub2 ,or sub1 stay but sub2=sub1;Consider 
special '0' case.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    int numDecodings(String s) {
        if (s.length()==0 || s.charAt(0) == '0') return 0;
	    // sub2: decode ways of s[i-2] ,sub1: decode ways of s[i-1] 
		int sub1 = 1, sub2 = 1;

		for (int i = 1; i < s.length(); i++) {
		// zero cannot be used separately
		    if (s.charAt(i) == '0') sub1 = 0;

			//  two-digit letter,sub1 sub2 update
	        if(s.charAt(i-1) == '1' || s.charAt(i-1) == '2'&&s.charAt(i) <= '6') {
			    sub1 = sub2 + sub1;
			    sub2 = sub1 - sub2;
			 }
			 // one-digit letter, sub1 no new way added
			 else sub2 = sub1;
			        
		 }
	return sub1;
	}
}


Same idea but reversed order and O(n) space:(easy process edge '0' cases)

public class Solution {
    public int numDecodings(String s) {
        int n = s.length();
        if (n == 0) return 0;

        int[] memo = new int[n+1];
        memo[n]  = 1;
        memo[n-1] = s.charAt(n-1) != '0' ? 1 : 0;

        for (int i = n - 2; i >= 0; i--)
            if (s.charAt(i) == '0') continue;
            else memo[i] = (Integer.parseInt(s.substring(i,i+2))<=26) ? memo[i+1]+memo[i+2] : memo[i+1];

        return memo[0];
    }
}

```
#### Reference:

---

