## Q23[ Merge k Sorted Lists ](https://leetcode.com/problems/merge-k-sorted-lists/) 

### Solution 1 Priority Queue
#### Idea:
Build a priority queue and define its sorted method(comparator),then put all heads of lists in this queue,
and when poll out a head and save,put in its next and then remained element in the priority queue for sorting process. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
         if (lists.length==0) return null;

        PriorityQueue<ListNode> queue= new PriorityQueue<ListNode>(1,new Comparator<ListNode>(){
           
            public int compare(ListNode o1,ListNode o2){
                if (o1.val<o2.val)
                    return -1;
                else if (o1.val==o2.val)
                    return 0;
                else 
                    return 1;
            }
        });

        ListNode res = new ListNode(0); 
        ListNode tail=res;

        for (ListNode node:lists)  //sort all heads of lists.
            if (node!=null)
                queue.add(node);

        while (!queue.isEmpty()){
        
        //remove the head(sorted element) of the queue, meanwhile save this element.
            tail.next=queue.poll(); 
            tail=tail.next;

            if (tail.next!=null)
                queue.add(tail.next);  //sort a new element.
        }
        return res.next;

    }
}
```

#### Reference:
[https://leetcode.com/discuss/9279/a-java-solution-based-on-priority-queue](https://leetcode.com/discuss/9279/a-java-solution-based-on-priority-queue)
---

