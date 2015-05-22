## Q18 [Four Sum](https://leetcode.com/problems/4sum/) 

### Solution 1 HashMap
#### Idea:
Class Pair is combination of two elements from num[]; use list to store the Pairs sum in same,build a map <sum/list> to store lists with different sum.
Finally,sweep this map, find the combination of lists(Pairs) sum in target.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n^2)
#### Source code:
```

public class Solution {
    public static class Pair {
        int a;
        int b;
        int aIndex;
        int bIndex;
        public Pair(int aInput, int aIndexInput, int bInput, int bIndexInput) {
            a = aInput;
            aIndex = aIndexInput;
            b = bInput;
            bIndex = bIndexInput;
        }

        public boolean same(Pair p) {
            return p != null && p.a == a && p.b == b;
        }
    }

    public List<List<Integer>> fourSum(int[] num, int target) {
        List<List<Integer>> fourSum = new ArrayList<>();
        if (num == null || num.length < 4) {
            return fourSum;
        }
       
        Arrays.sort(num);
        TreeMap<Integer, List<Pair>> map = new TreeMap<>();
        for (int i = 0; i < num.length - 1; i++) {
            for (int j = i + 1; j < num.length; ) {
                int sum = num[i] + num[j];
                List<Pair> list;
                if (map.containsKey(sum)) {
                    list = map.get(sum);
                } else {
                    list = new ArrayList<>();
                    map.put(sum, list);
                }
                list.add(new Pair(num[i], i, num[j], j));
                do {                 // avoid extended duplicated pair ,for ex.[22234555678],in this way instead of 3 times, 
                    j++;              //[2,2] will store 2 times,and later will cut the other one time.

                } while (j < num.length && num[j] == num[j - 1]);  
            }
        }

        Integer low = map.firstKey();
        Integer high = map.lastKey();
        while (low != null && high != null && low <= high) {
            if (low + high < target) {
                low = map.higherKey(low);     //larger value of key
            } else if (low + high > target) {
                high = map.lowerKey(high);    //smaller value of key
            } else {
               
     //below, avoid all duplicated pairs,find all two combined pairs sum in the same,like i j loop.

               Pair lastA = null;
                  for (Pair a : map.get(low)) {  
                     if (a.same(lastA)) {
                        continue;
                     }
                     lastA = a; // saved,ensure that the same sum but DIFFERENT pair.

                     Pair lastB = null;
                     for (Pair b : map.get(high)) {   //avoid all duplicated pairs.
                         if (a.bIndex < b.aIndex) {  //this condition is toavoid duplicated cout of elements.GENERALLY,
                                                    // when pick 4 elements, your are supposed to  pick in order.
                            if (b.same(lastB)) {
                                continue;
                            }
                            lastB = b;
                            fourSum.add(Arrays.asList(a.a, a.b, b.a, b.b));
                         }
                   }
               }

                low = map.higherKey(low);
                high = map.lowerKey(high);
            }
        }

        return fourSum;
    }
}


```
#### Reference:

---

