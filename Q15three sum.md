## Q15 [3 Sum](https://leetcode.com/problems/3sum/) 

### Solution 1 HashSet
#### Idea:
first sort the array, then run through all possible first element of a triplet. For each possible first element  make a  2Sum sweep of the remaining part of the array.
in order to sum 0,for the 3 elements ,get the larger number toward right  or get the smaller number toward left.
And utilize hashset to avoid duplicated result.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public List<List<Integer>> threeSum(int[] num) {
    Arrays.sort(num);
    List<List<Integer>> list = new ArrayList<List<Integer>>();
    HashSet<List<Integer>> set = new HashSet<List<Integer>>();
    for(int i=0;i<num.length;i++)
    {
        for(int low=i+1,high=num.length-1;low<high;)
        {
            if(num[i]+num[low]+num[high]==0)
            {
                List<Integer> lists= new ArrayList<Integer>();
                lists.add(num[i]);
                lists.add(num[low]);
                lists.add(num[high]);
                if(set.add(lists))
                list.add(lists);
                low++;
                high--;
            }
            else if(num[i]+num[low]+num[high]<0)
            low++;
            else
            high--;
        }
    }
    return list;
  }
}
```
#### Reference:

---
### Solution 2 
#### Idea: sort the array, then run through all indices of a possible first element of a triplet,meanwhile skip the duplicated number.
For each possible first element  make a  2Sum sweep of the remaining part of the array.
in order to sum 0,for the 3 elements ,get the larger number toward right  or get the smaller number toward left.

#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public List<List<Integer>> threeSum(int[] num) {
    Arrays.sort(num);
    List<List<Integer>> res = new ArrayList<List<Integer>>(); 
    for (int i = 0; i < num.length-2; i++) {
        if (i == 0 || (i > 0 && num[i] != num[i-1])) {
            int low = i+1, high = num.length-1, sum = 0 - num[i];
            while (low < high) {
                if (num[low] + num[high] == sum) {
                    res.add(Arrays.asList(num[i], num[low], num[high]));
                    while (low < high && num[low] == num[low+1]) low++;
                    while (low < high && num[high] == num[high-1]) high--;
                    low++; high--;
                } else if (num[low] + num[high] < sum) low++;
                else high--;
           }
        }
    }
    return res;
}

}
```
#### Reference:

---
