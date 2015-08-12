## Q207[Course Schedule ](https://leetcode.com/problems/course-schedule/) 

### Solution 1 Topological Sort,Backtrack
#### Idea:
Use a graph of  two dimensional list to mark the courses and  prerequisite courses ,search if there is a circle(false).
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        ArrayList[] graph = new ArrayList[numCourses];
        for(int i=0;i<numCourses;i++)  
            graph[i] = new ArrayList();
        boolean[] cycStart = new boolean[numCourses];
        for(int i=0; i<prerequisites.length;i++)
            graph[prerequisites[i][1]].add(prerequisites[i][0]);
        
        //initiate first course    
        for(int i=0; i<numCourses; i++){
            if(!backtrack(graph,cycStart,i))
                return false;
        }
        return true;
    }

    private boolean backtrack(ArrayList[] graph, boolean[] cycStart, int pick){
        if(cycStart[pick])  //find a cycle.
            return false;
        // base on cycle start array,search if there is a cycle by DFS.    
        cycStart[pick] = true;
        for(int i=0; i<graph[pick].size();i++){
            if(!backtrack(graph,cycStart,(int)graph[pick].get(i)))
                return false;
        }
        cycStart[pick] = false;
        
        return true;
    }
}
```
#### Reference:
---

