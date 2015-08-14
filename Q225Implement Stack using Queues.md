## Q225[Implement Stack using Queues ](https://leetcode.com/problems/implement-stack-using-queues/) 

### Solution 1 Queue
#### Idea:
Straight forward.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
class MyStack {
    Queue<Integer> q = new LinkedList<Integer>(); 
    // Push element x onto stack.
    public void push(int x) {
        q.offer(x);
    }

    // Removes the element on top of the stack.
    public void pop() {
        for(int i=0;i<q.size()-1;i++){
            q.offer(q.poll());
        }
        q.poll();
    }

    // Get the top element.
    public int top() {
         for(int i=0;i<q.size()-1;i++){
           q.offer(q.poll());
         }
        int tmp=q.poll();
        q.offer(tmp);
        return tmp;
    }

    // Return whether the stack is empty.
    public boolean empty() {
        return (q.isEmpty());
    }
}
```
#### Reference:
---

