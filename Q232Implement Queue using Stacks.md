## Q232[Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) 

### Solution 1 Stack
#### Idea:
Pay a attention that stack.size() will change in for loop.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
class MyQueue {
    Stack<Integer> s=new Stack<Integer>();
    // Push element x to the back of queue.
    public void push(int x) {
        s.push(x);
    }

    // Removes the element from in front of queue.
    public void pop() {
        int size=s.size();  // attention,s.size() in for loop will change!
        Stack<Integer> tmp=new Stack<Integer>();
        for(int i=0;i<size-1;i++){  
            tmp.push(s.pop());
        }
        s.pop();
        while(!tmp.isEmpty()) s.push(tmp.pop());
        
    }

    // Get the front element.
    public int peek() {
        int size=s.size();  
        Stack<Integer> tmp=new Stack<Integer>();
        for(int i=0;i<size-1;i++){
            tmp.push(s.pop());
        }
        int res=s.peek();
        while(!tmp.isEmpty()) s.push(tmp.pop());
        return res;
    }

    // Return whether the queue is empty.
    public boolean empty() {
        return s.isEmpty();
    }
}
```
#### Reference:
---

