## Q155[Min Stack ](https://leetcode.com/problems/min-stack/) 

### Solution 1 
#### Idea:
Build two stacks,one for function push ,pop,top ,and the other for getMin recording min elements in stack when push or pop.  
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
class MinStack {
    private Stack<Integer> stack = new Stack<Integer>();
    private Stack<Integer> minStack = new Stack<Integer>();
    
    public void push(int x) {
        stack.push(x);
        if(minStack.isEmpty() || x <= minStack.peek()){
        minStack.push(x);
        }
    }
    public void pop() {
        int x=minStack.peek();
        int y=stack.peek();
        if( y== x){  //sides of"=="can not be XXX.peak() simultaneously.
        minStack.pop();
        }
        stack.pop();
    }
    public int top() {
        return stack.peek();
    }
    public int getMin() {
        return minStack.peek();
    }
}

```
#### Reference:

---

