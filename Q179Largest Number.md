## Q179[Largest Number](https://leetcode.com/problems/largest-number/) 

### Solution 1 
#### Idea:
Override comparator for sort depending on String.compareTo.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
   public  String largestNumber(int[] num) {
     if(num==null || num.length==0)
        return "";
     String[] tmp = new String[num.length];
     for(int i=0;i<num.length;i++)
        tmp[i] = num[i]+"";
     Comparator<String> comparator = new Comparator<String>(){
        @Override
        public int compare(String str1, String str2){
            String s1 = str1+str2;
            String s2 = str2+str1;
            return s2.compareTo(s1);
        }
     };
     Arrays.sort(tmp,comparator);
     if(tmp[0].charAt(0)=='0')
        return "0";

     StringBuilder sb = new StringBuilder();
     for(String s: tmp)  sb.append(s);
     return sb.toString();
   }
}
```
#### Reference:
---

