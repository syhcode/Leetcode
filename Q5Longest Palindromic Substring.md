## Q5[Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) 

### Solution 1 
#### Idea:
Judge a palindrome begin from its mid in two cases.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    private int maxLength = 1;
    private int maxIndex = 0;
    public String longestPalindrome(String str) { 
        int length = str.length();
        for (int i=0; i<length; i++) {
            // find longest odd palindrome with center i
            findPalindrome(str, length, i, 0);
            // find longest even palindrome with center i
            findPalindrome(str, length, i, 1);
        }
        return str.substring(maxIndex, maxIndex+maxLength);
    }

    private void findPalindrome(String str, int length, int i, int shift) {
        int left = i;
        int right= i+shift;
        while (left >= 0 && right < length && str.charAt(left) == str.charAt(right)) {
             if ((right - left + 1) > maxLength) {
                maxLength = right - left + 1;
                maxIndex = left;
             }
        left--;
        right++;
        }
   }
}

```
#### Reference:

---

