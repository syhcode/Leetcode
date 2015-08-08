## Q164[ Maximum Gap ](https://leetcode.com/problems/maximum-gap/) 

### Solution 1 Bucket Sort
#### Idea:
```
Use Bucket Sort can make Time Complexity in n costing extra n memory.

Then the maximum gap will be no smaller than ceiling[(B - A) / (N - 1)]

Let the length of a bucket to be len = ceiling[(B - A) / (N - 1)], 
then we will have at most num = (B - A) / len + 1 of bucket.

for any number K in the array, we can easily find out which bucket it belongs by calculating 
(K - A) / len and therefore maintain the maximum and minimum elements in each bucket.

Since the maximum difference between elements in the same buckets will be at most len - 1, 
so the final answer will not be taken from two elements in the same buckets.

For each non-empty buckets p, find the next non-empty buckets q, then q.min - p.max 
could be the potential answer to the question. 
```

#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int maximumGap(int[] num) {
        if(num==null||num.length<2) return 0;
        int len = num.length;
        int min = 0;
        int max = 0;
        for(int i = 0; i < len; i++){
            min = Math.min(min, num[i]);
            max = Math.max(max, num[i]);
        }
        int bucketLen= (max-min)/(len-1) + ((max-min)%(len-1)>0?1:0); //bucket gap
        int bucketCount = (max-min)/bucketLen + 1;
        int[] minBuckets = new int[bucketCount];
        int[] maxBuckets = new int[bucketCount];

        Arrays.fill(minBuckets, Integer.MAX_VALUE);
        Arrays.fill(maxBuckets, Integer.MIN_VALUE);
        
        // elements in every bucketLen range,the min one in minBucket,the max one in maxBucket.
        //use two buckets can easily find successive elements' diffrence,meanwhile reduce compare times. 
        for(int i = 0; i < len; i++){
            int idx = (num[i] - min)/bucketLen;
            minBuckets[idx] = Math.min(minBuckets[idx], num[i]);
            maxBuckets[idx] = Math.max(maxBuckets[idx], num[i]);
        }
        //since the maxGap can not < bucketLen,thus can find it bwtween two bucket.
        int maxGap = 0;
        int prev = maxBuckets[0];
        for(int i = 1; i < bucketCount; i++){
            if(minBuckets[i]==Integer.MAX_VALUE&&maxBuckets[i]==Integer.MIN_VALUE) continue;
            maxGap = Math.max(maxGap, minBuckets[i] - prev);
            prev = maxBuckets[i];
        }
        return maxGap;
    }
}

```
#### Reference:
---

