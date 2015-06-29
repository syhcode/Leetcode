## Q138[ Copy List with Random Pointer ](https://leetcode.com/problems/copy-list-with-random-pointer/) 

### Solution 1 Hashmap
#### Idea:
Build hash map to store (node image,new this node), then depending on origin nodes connection link new nodes in hash map.
In this way the common O(n^2) time(to get random linked position) solution can be reduce to O(n) time.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for singly-linked list with a random pointer.
 * class RandomListNode {
 *     int label;
 *     RandomListNode next, random;
 *     RandomListNode(int x) { this.label = x; }
 * };
 */
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
         HashMap<RandomListNode, RandomListNode> maps = new HashMap<RandomListNode, RandomListNode>();
         RandomListNode cursor = head;
             //build new copied node and define val and random.
        while(null != cursor){
            maps.put(cursor, new RandomListNode(cursor.label));
            cursor = cursor.next; 
        }
             cursor = head;
        while(null != cursor){
            maps.get(cursor).random = maps.get(cursor.random);
            cursor = cursor.next;
         }
             cursor = head;
             
             //define link for new builded nodes.
        while(null != cursor){
            maps.get(cursor).next = maps.get(cursor.next);
            cursor = cursor.next;
        }
        return maps.get(head);
    }
}
```
#### Reference:

---

