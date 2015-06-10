## Q57 [Insert Interval ](https://leetcode.com/problems/insert-interval/) 

### Solution 1 
#### Idea:  
The new interval has 4 situations: 1 at begin no overlap; 2 overlap between lists in the list;
3 not overlap between lists in the list; 4 at end no overlap. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
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
    public List<Interval> insert(List<Interval> intervals, Interval newInterval) {
        int left;
        int right;
        int len=intervals.size();
        List<Interval> result=new ArrayList<Interval>();
        if(len==0){
        result.add(new Interval(newInterval.start,newInterval.end));
        return result;
        }
        if(newInterval.end<intervals.get(0).start)   //put it at begin
        result.add(new Interval(newInterval.start,newInterval.end));
               
        for(int i=0;i<len;i++){   // newInterval overlap with Intervals[i]
            if(newInterval.start<=intervals.get(i).end&&newInterval.end>=intervals.get(i).start) {
                left=Math.min(intervals.get(i).start,newInterval.start);
                while(newInterval.end>intervals.get(i).end&&i<len-1&&newInterval.end>=intervals.get(i+1).start) i++;
                right=Math.max(intervals.get(i).end,newInterval.end);
                result.add(new Interval(left,right)); 
                i++;
            
            }
                             //not overlap
            else if(newInterval.start>intervals.get(i).end&&i<len-1&&newInterval.end<intervals.get(i+1).start){
                   result.add(intervals.get(i));
                   i++;
                   result.add(new Interval(newInterval.start,newInterval.end));
            }
            
            if(i<=len-1)
             result.add(intervals.get(i));
            
        }
        if(newInterval.start>intervals.get(len-1).end) //put it at end
        result.add(new Interval(newInterval.start,newInterval.end));
        return result;
        
    }
}
```
#### Reference:

---

