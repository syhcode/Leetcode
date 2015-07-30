## Q218[The Skyline Problem](https://leetcode.com/problems/the-skyline-problem/) 

### Solution 1 Priority Queue,Tree Map.
#### Idea:
Use priority queque to store and sort the left and right edge height respectively.When left or right edge height are same,
sort left in descending order and right in ascending order to make sure that highest height will cover all short and get priority to store in result. 
Use a Tree Map to update the current highest left (left edge is removed by same height right edge). Store the current max height in result.
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public List<int[]> getSkyline(int[][] buildings) {
        PriorityQueue<Point> points=new PriorityQueue<Point>(new Comparator<Point>(){
            public int compare(Point a, Point b){ //ascending,smaller in priority.
                if(a.x!=b.x)
                    return a.x-b.x;
                return a.y-b.y;
            }
        });
        TreeMap<Integer, Integer> heights=new TreeMap<Integer, Integer>();
        ArrayList<int[]> result=new ArrayList<>();
        // use'-' to separate left and right edge.
        
        for(int[] building: buildings){
            points.add(new Point(building[0], -building[2]));
            points.add(new Point(building[1], building[2]));
        }
        heights.put(0, 1);
        int maxHeight=0;
        // store  current highest height in result,and wait when it is covered or removed 
        // by the same value right edge.
        
        while(!points.isEmpty()){
            Point point=points.poll();
            if(point.y<0){ //left edge
                if(!heights.containsKey(-point.y))
                    heights.put(-point.y, 1);
                else heights.put(-point.y, heights.get(-point.y)+1); //same height edge
            }
            else{
                heights.put(point.y, heights.get(point.y)-1);
                if(heights.get(point.y)==0) heights.remove(point.y);
            }
            // get current highest height.
            
            int currentMax=heights.lastEntry().getKey();
            if(currentMax!=maxHeight){
                result.add(new int[]{point.x, currentMax});
                maxHeight=currentMax;
            }
        }
        return result;
    }
    private class Point{
        int x;
        int y;
        public Point(int x, int y){
            this.x=x;
            this.y=y;
        }
    }
}

```
#### Reference:
[java Tree Map](http://blog.csdn.net/speedme/article/details/22661671)
---

