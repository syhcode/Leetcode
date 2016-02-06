## Q295[Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) 

### Solution 1 heap
#### Idea:
one min heap and one max heap, poll from max heap to the min, keep their size equal and return peek();
#### Time Complexity:
O(logn)
#### Space Complexity:
O(n)
#### Source code:
```
class MedianFinder {
    // max queue is always larger or equal to min queue
    PriorityQueue<Integer> min = new PriorityQueue();
    PriorityQueue<Integer> max =new PriorityQueue<Integer>(new Comparator<Integer>(){
			public int compare(Integer i1, Integer i2){ //override constructor
			return i2-i1;
			}
		}
			);
    // Adds a number into the data structure.
    public void addNum(int num) {
        max.offer(num);
        min.offer(max.poll());
        if (max.size() < min.size()){
            max.offer(min.poll());
        }
    }
    // Returns the median of current data stream
    public double findMedian() {
        if (max.size() == min.size()) return (max.peek() + min.peek()) /  2.0;
        else return max.peek();
    }
};

// Your MedianFinder object will be instantiated and called as such:
// MedianFinder mf = new MedianFinder();
// mf.addNum(1);
// mf.findMedian();

```
#### Reference:

---

