## Q205[Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/) 

### Solution 1 Hashmap 
#### Idea:
Simultaneously process two strings, use Hashmap to store different chars and their positions,and
do judgment of two Strings that if current char exist before and is the same char (at the same position).  
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean isIsomorphic(String s, String t) {
        Map<Character,Integer> maps=new HashMap<Character,Integer>();
        Map<Character,Integer> mapt=new HashMap<Character,Integer>();
        for(int i=0;i<s.length();i++){
            char tmp1=s.charAt(i);
            char tmp2=t.charAt(i);

            if(maps.containsKey(tmp1)&&mapt.containsKey(tmp2)){
            //auto-unboxing process,Integer->int;
                int ind1=maps.get(tmp1);
			    int ind2=mapt.get(tmp2);
                if(ind1!=ind2) return false;
            }
            else if(!maps.containsKey(tmp1)&&!mapt.containsKey(tmp2)){
            maps.put(tmp1,i); mapt.put(tmp2,i);
            }
            else return false;
        }
    return true;    
    }
}
```
#### Reference:
[java boxing](http://denverj.iteye.com/blog/745422)
---

