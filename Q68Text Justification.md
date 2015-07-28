## Q68[Text Justification](https://leetcode.com/problems/text-justification/) 

### Solution 1 Recursive
#### Idea:
Build String line by line. Add first word in a line, then initiate one head space
for each word, then if it is one word line or last line: append all rear space; 
if not append the remained space in every head space.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<String> fullJustify(String[] words, int L) {
        List<String> list = new LinkedList<String>();
        //"" count as one word
        for (int i = 0, w; i < words.length; i = w) {
            int len = -1;
            for (w = i; w < words.length && len + words[w].length() + 1 <= L; w++) {
                len += words[w].length() + 1;
            }
            StringBuilder strBuilder = new StringBuilder(words[i]);
            
            //each word in a line is with one head space  
            int space = 1, extra = 0;
            // except one word a line or last line, append " " in every head space.
            if (w != i + 1 && w != words.length) { 
               space = (L - len) / (w - i - 1) + 1;
               extra = (L - len) % (w - i - 1);
            }
            for (int j = i + 1; j < w; j++) {
                for (int s = space; s > 0; s--) strBuilder.append(' ');
                if (extra-- > 0) strBuilder.append(' ');
                strBuilder.append(words[j]);
            }
            
            //left justified: the last line or one word line rear append " " to full L
            int strLen = L - strBuilder.length();
            while (strLen-- > 0) strBuilder.append(' ');
            list.add(strBuilder.toString());
        }

        return list;
    }
}
#### Reference:

---

