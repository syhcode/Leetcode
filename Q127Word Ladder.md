## Q127[Word Ladder](https://leetcode.com/problems/word-ladder/) 

### Solution 1 BFS,Queue
#### Idea:
Move words(in dictionary) with only ONE different char with the former words(group) into stack, and base on these words
in stack to match remained words in dictionary changing one char, and update the words in stack. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int ladderLength(String start, String end, Set<String> dict) {
    LinkedList<String> queue = new LinkedList<String>();
    queue.add(start);
    dict.add(end);
    int step = 0;

    while (!queue.isEmpty()) {
        LinkedList<String> nextGroup = new LinkedList<String>();
        step++; 
        
        while (!queue.isEmpty()) {
            String q = queue.poll();
            if(q.equals(end))
                return step;
            // find a word if match dict if change a character.
            char[] str = q.toCharArray();
            for(int i = 0; i < start.length(); i++){
                for(char c = 'a'; c <= 'z'; c++){
                    char temp = str[i];
                    str[i] = c;
                    String s = String.valueOf(str); //if use substring method will get TLE
                    str[i] = temp;
                    if(dict.contains(s)){
                        nextGroup.add(s); //next group match more char than former
                        dict.remove(s);  //delete the matched word(in nextGroup)
                    }
                }
            }
        }
        queue = nextGroup; //a new turn to match
    }
    return 0; //not found q.equals(end) in searching.
  }
}
```
#### Reference:
---

