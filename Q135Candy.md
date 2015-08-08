## Q135[Candy](https://leetcode.com/problems/candy/) 

### Solution 1 
#### Idea:
For an ascending array,count its size and find the total candy.For an descending array,count its size and find the tatal candy,
but should up-level its head(the rear of ascending array) considering its size is bigger than the former ascending size. 
When meet a equal element,set one candy and regard as one element ascending array.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int candy(int[] ratings) {
        if (ratings == null || ratings.length == 0) return 0;
        int total = 1,up = 1, down = 0;
        for (int i = 1; i < ratings.length; i++) {
            if (ratings[i] >= ratings[i-1]) {
                if (down > 0) {
                    total += down*(down+1)/2; // count
                    if (down >= up) total += down - up + 1; //up-level head
                    down = 0;
                    up = 1; //reset ascending array 
                }
                // equal element count as one element ascending array.
                up = ratings[i] == ratings[i-1] ? 1 : up+1;
                total += up;
            } else down++;
        }
        if (down > 0) { // deal descending array at the end
            total += down*(down+1)/2;
            if (down >= up) total += down - up + 1;
        }
        return total;
    }
}
```
#### Reference:
---

