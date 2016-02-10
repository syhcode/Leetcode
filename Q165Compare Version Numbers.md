## Q165[Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/) 

### Solution 1
#### Idea:
Split two String by"\\\\." and compare sections; use 0 to compare with remained array.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int compareVersion(String version1, String version2) {
    String[] levels1 = version1.split("\\.");
    String[] levels2 = version2.split("\\.");

    int length = Math.max(levels1.length, levels2.length);
    for (int i=0; i<length; i++) {
        Integer v1 = i < levels1.length ? Integer.valueOf(levels1[i]) : 0;
        Integer v2 = i < levels2.length ? Integer.valueOf(levels2[i]) : 0;
        int compare = v1.compareTo(v2);
        if (compare != 0) {
            return compare;
        }
    }
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

