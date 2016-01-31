## Q284 [Peeking Iterator](https://leetcode.com/problems/peeking-iterator/) 

### Solution 1 
#### Idea:
record the peek() process, which move forward the pointer and thus we need to delay the next();
#### Time Complexity:
O(1)
#### Space Complexity:
O(1)
#### Source code:
```
// Java Iterator interface reference:
// https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html

//https://github.com/google/guava/blob/703ef758b8621cfbab16814f01ddcc5324bdea33/guava-gwt/src-super/com/google/common/collect/super/com/google/common/collect/Iterators.java#L1125

class PeekingIterator implements Iterator<Integer> {
    Integer peek=null;
    boolean hasPeek = false;
    Iterator<Integer> iter; // private final Iterator<? extends E> iterator;
	public PeekingIterator(Iterator<Integer> iterator) {
	    // initialize any member here.
	    iter=iterator;
	}
    // Returns the next element in the iteration without advancing the iterator.
	public Integer peek() {
	   if(!hasPeek){
	      hasPeek = true;     
	      peek=iter.next(); // this always return null at end pos.
	      return peek;
	   }else{
	      hasPeek = true; 
	      return peek;
	   }
	}
	// hasNext() and next() should behave the same as in the Iterator interface.
	// Override them if needed.
	@Override
	public Integer next() {
	    if(hasPeek) { 
	        hasPeek = false; 
	        return peek; 
	    } else return iter.next();
	}
	@Override
	public boolean hasNext() {
	    if(hasPeek) return peek!=null;
	    else return iter.hasNext();
	}
}

```
#### Reference:

---

