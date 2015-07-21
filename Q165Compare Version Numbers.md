## Q165[Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/) 

### Solution 1
#### Idea:
Split two String by"\\." and compare sections.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int compareVersion(String version1, String version2) {
        String[] s1=version1.split("\\.");
        String[] s2=version2.split("\\.");
        int len=Math.min(s1.length,s2.length);
        for(int i=0;i<len;i++){
            int num1=Integer.parseInt(s1[i]);
            int num2=Integer.parseInt(s2[i]);
            if(num1>num2) return 1;
            if(num1<num2) return -1;
        }
        if(s1.length>s2.length&&Integer.parseInt(s1[len])!=0)
             return 1;
        if(s1.length<s2.length&&Integer.parseInt(s2[len])!=0)
            return -1;
        return 0;
    }
}
```
#### Reference:
```
[String methods](http://blog.csdn.net/az44yao/article/details/7582580)
The method split() depend on method matches() and RE.
Dealing with \(split("\\\\")),  |  .  ( )  [ ]  ^  $  -  * should append "//".

```

