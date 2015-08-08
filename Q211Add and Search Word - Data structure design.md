## Q211[Add and Search Word - Data structure design](https://leetcode.com/problems/add-and-search-word-data-structure-design/) 

### Solution 1 TrieTree,Recursive
#### Idea:
Use TrieTree(a position index based storage structure) to accelerate search. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class WordDictionary {
    // initialize date structure.
    public class TrieNode {
        public TrieNode[] children = new TrieNode[26];
        public String item = "";
    }
    
    private TrieNode root = new TrieNode();
    
    // apply addWord().
    public void addWord(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            if (node.children[c - 'a'] == null) {
                node.children[c - 'a'] = new TrieNode();
            }
            node = node.children[c - 'a'];
        }
        node.item = word; // the TrieTree end with a word,suggest a word end.
    }
    // apply search().
    public boolean search(String word) {
        return match(word.toCharArray(), 0, root);
    }

    private boolean match(char[] chs, int k, TrieNode pre) {
        if (k == chs.length) return !pre.item.equals(""); //the final last node is the target word.  
        if (chs[k] != '.') {
          return pre.children[chs[k] - 'a'] != null && match(chs, k + 1, pre.children[chs[k] - 'a']);
        } else {
            //if '.', step in all this level TrieNodes existed.
            for (int i = 0; i < 26; i++) {
                if (pre.children[i] != null) {
                    if (match(chs, k + 1, pre.children[i])) {
                        return true;
                    }
                }
            }
        }
        return false;
    }
}
```
#### Reference:
---

