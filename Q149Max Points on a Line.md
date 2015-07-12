## Q149[Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/) 

### Solution 1 Hashmap
#### Idea:
Judge points one by one.For one point[i],set it as a basement and depend on smallest integer pair (as slope)
to judge if other points[j] is at same line with this point[i].
Hashmap<x...,<y...,number of y...>> helps to count the max points with points[i] on a line. 
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for a point.
 * class Point {
 *     int x;
 *     int y;
 *     Point() { x = 0; y = 0; }
 *     Point(int a, int b) { x = a; y = b; }
 * }
 */
/*
     *  A line is determined by two factors,say y=ax+b
     *  
     *  If two points(x1,y1) (x2,y2) are on the same line(Of course). 

     *  Consider the gap between two points.

     *  We have (y2-y1)=a(x2-x1),a=(y2-y1)/(x2-x1) a is a rational, b is canceled since b is a constant

     *  If a third point (x3,y3) are on the same line. So we must have y3=ax3+b

     *  Thus,(y3-y1)/(x3-x1)=(y2-y1)/(x2-x1)=a

     *  Since a is a rational, there exists y0 and x0, y0/x0=(y3-y1)/(x3-x1)=(y2-y1)/(x2-x1)=a

     *  So we can use y0&x0 to track a line;
     */

    public class Solution{
        public int maxPoints(Point[] points) {
            if (points==null) return 0;
            if (points.length<=2) return points.length;

            Map<Integer,Map<Integer,Integer>> map = new HashMap<Integer,Map<Integer,Integer>>();
            int result=0;
            for (int i=0;i<points.length;i++){ 
                map.clear();
                int overlap=0,max=0;
                for (int j=i+1;j<points.length;j++){
                    int x=points[j].x-points[i].x;
                    int y=points[j].y-points[i].y;
                    if (x==0&&y==0){
                        overlap++;
                        continue;
                    }
                    // get the greatest common divisor
                    int gcd=generateGCD(x,y);
                    if (gcd!=0){
                        x/=gcd;
                        y/=gcd;
                    }
                    // since same x may have different y 
                    if (map.containsKey(x)){
                        if (map.get(x).containsKey(y)){
                            map.get(x).put(y, map.get(x).get(y)+1);
                        }else{
                            map.get(x).put(y, 1);
                        }                       
                    }else{
                        Map<Integer,Integer> m = new HashMap<Integer,Integer>();
                        m.put(y, 1);
                        map.put(x, m);
                    }
                    //max is the max number of points that are in same line with points[i]; 
                    max=Math.max(max, map.get(x).get(y));
                }
                    // the total number of points at the same line( with points[i]), 
                    // "overlap+1" is the number of points at points[i].
                result=Math.max(result, max+overlap+1);
            }
            return result;
        }
        
        private int generateGCD(int a,int b){

            if (b==0) return a;
            else return generateGCD(b,a%b);

        }
    }
```
#### Reference:

---

