## Q56 [Merge Intervals](https://leetcode.com/problems/merge-intervals/) 

### Solution 1 
#### Idea:
Ascending sort intervals by start element,then two if one's end > the next's start.
#### Time Complexity:
Sort:O(nlog(n)); Merge:O(n); all O(nlog(n));
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for an interval.
 * public class Interval {
 *     int start;
 *     int end;
 *     Interval() { start = 0; end = 0; }
 *     Interval(int s, int e) { start = s; end = e; }
 * }
 */


public class Solution {
   public List<Interval> merge(List<Interval> intervals) {
    if (intervals.size() <= 1)
        return intervals;

// (ascendind) Sort method depend on the value of function compare(), 
//compare() describes the two neiboor values camparing.
    
    Collections.sort(intervals, new Comparator<Interval>() {
 //override comparator<>()
        public int compare(Interval a, Interval b) {
            return Integer.compare(a.start, b.start);
        }
    });

        List<Interval> result = new ArrayList<Interval>();
        int start = intervals.get(0).start;
        int end = intervals.get(0).end;

    for (int i=1;i<intervals.size();i++) {
        if (intervals.get(i).start<=end)
            end = Math.max(end, intervals.get(i).end);
        else {                     
            result.add(new Interval(start, end));
            start = intervals.get(i).start;
            end = intervals.get(i).end;
        }
    }


    result.add(new Interval(start, end));
    return result;
  }

}

```
#### Reference:

---

