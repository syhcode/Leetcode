## Q49[Anagrams](https://leetcode.com/problems/anagrams/) 

### Solution 1 Hashmap
#### Idea:
First saved sorted string(uniform key) in hash map, and save its position in String[], then when find a same sorted string,
it is a anagram with a former one and save its position in key's  corresponding ArrayList<Integer>.Finally depend on these 
position bulid the anagram List.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    HashMap<String, ArrayList<Integer>> hashmap = new HashMap<String, ArrayList<Integer>>();
    public List<String> anagrams(String[] strs) {
         ArrayList<String> res = new ArrayList<String>();
    
    // build a hash table, with the "unique" string form (uniform sorted anagram)as the key
         for(int i=0; i<strs.length; ++i){
         
            char [] charArray = strs[i].toCharArray();
            Arrays.sort(charArray);           
            String key = String.valueOf(charArray);
            ArrayList<Integer> value = hashmap.get(key);
            if(value == null){
                 value = new ArrayList<Integer>();
                 value.add(i);
                 hashmap.put(key, value);
            }else{
                 value.add(i);
            }
         }
    // get anagrams by index from the hashmap.

        for(String key:hashmap.keySet()){
            ArrayList<Integer> indexList = hashmap.get(key);
            if(indexList.size() > 1){
                 for(Integer i : indexList){
                     res.add(strs[i]);
                 }
            }
        }
    return res;
    }
}
```
#### Reference:

---

