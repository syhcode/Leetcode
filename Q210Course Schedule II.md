## Q210[Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) 

### Solution 1 BFS,Queue,Iterative
#### Idea:
There must be one course without pre-course at beginning.
After pick it,there also should be a course unlocked if there is a solution, and do this iteratively. 
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int[] findOrder(int numCourses, int[][] prerequisites) {
    ArrayList<HashSet<Integer>> graph = new  ArrayList<HashSet<Integer>>();
    for(int i=0;i<numCourses;i++)
        graph.add(new HashSet<Integer>());

    for(int i=0;i<prerequisites.length;i++){
        graph.get(prerequisites[i][1]).add(prerequisites[i][0]);
    }

    int[] holds = new int[numCourses];
    for(int i=0;i<graph.size();i++){ // course x require holds[x] pre-course.
        for(int x:graph.get(i))
             holds[x]++;
    }

    LinkedList<Integer> queue = new LinkedList<Integer>();
    for(int i=0;i<numCourses;i++){
        if(holds[i] == 0){  // begin to pick one without pre-course.
            queue.offer(i);
        }
    }
    int[] res = new int[numCourses];
    int count = 0;
    while(!queue.isEmpty()){
        // since each time will poll out a course and add to result,
        //there is only one result depending on first ele in queue.
        int cur = queue.pollFirst();
        for(int c : graph.get(cur)){
            if(--holds[c] == 0)
                queue.offer(c);
        }

        res[count++] = cur;
    }
    return count==numCourses? res: new int[0];
  }
}
```
#### Reference:
---

