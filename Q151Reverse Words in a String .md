## Q151[Reverse Words in a String ](https://leetcode.com/problems/reverse-words-in-a-string/) 

### Solution 1 Recursive
#### Idea:
First reverse string, then reverse word one by one meanwhile add ' ' in word rear.
If string end with ' ', avoid this space. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public String reverseWords(String s) {
   // reverse the whole string and convert to char array
    char[] str = reverse(s.toCharArray(), 0, s.length()-1);
    int start = 0, end = 0; 
    for (int i = 0; i < str.length; i++) {
        if (str[i] != ' ') { 
            str[end++] = str[i]; 
        } //first space after a word
        else if (i > 0 && str[i-1] != ' ') {
            reverse(str, start, end-1); 
            str[end++] = ' '; 
            start = end; 
        }
    }
    //consider no space in rear of the last word.
    reverse(str, start, end-1); 
    return new String(str, 0, end > 0 && str[end-1] == ' ' ? end-1 : end);
  }
  public char[] reverse(char[] arr, int i, int j) {
    while (i < j) {
        char tmp = arr[i];
        arr[i++] = arr[j];
        arr[j--] = tmp;
    }
    return arr;
  }
}
```
#### Reference:

---

