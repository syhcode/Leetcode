## Q76[Minimum Window Substring ](https://leetcode.com/problems/minimum-window-substring/) 

### Solution 1 Two Pointer
#### Idea:
Sweep and store every T elements's amount in Tmap[] in its char-position, in the same way process S in Smap[] with pointer j for rear,i for head.
If S(rear j) has all the T's elements, the pointer i and pointer j make a substring, then move i until Smap[] lack enough amount of corresponding number
in Tmap[], begin a new search turn and may get the smaller substring.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
 public String minWindow(String S, String T) {
    if(S==null||S.isEmpty()||T==null||T.isEmpty()) return "";
    int i=0, j=0;
    int[] Tmap=new int[256];
    int[] Smap=new int[256];
    for(int k=0; k< T.length(); k++){
        Tmap[T.charAt(k)]++;
    }
    int found=0;
    int length=Integer.MAX_VALUE;
    String res="";
    while(j<S.length()){
      // move j(rear) until find enough element correspond to T.  
        if(found<T.length()){
            if(Tmap[S.charAt(j)]>0){
                Smap[S.charAt(j)]++;
                if(Smap[S.charAt(j)]<=Tmap[S.charAt(j)]){
                    found++;
                }
            }
            j++;
        }
      //move i(head) until the found string lack a element correspond to T.    
        while(found==T.length()){
            if(j-i<length){
                length=j-i; res=S.substring(i,j);
            }
            if(Tmap[S.charAt(i)]>0){
                Smap[S.charAt(i)]--;
                if(Smap[S.charAt(i)]<Tmap[S.charAt(i)]){
                    found--;
                }
            }
            i++;
        }
    }
    return res;
 }

}
```
#### Reference:

---

