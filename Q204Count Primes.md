## Q204[Count Primes](https://leetcode.com/problems/count-primes/) 

### Solution 1 Sieve of Eratosthenes
#### Idea:
Explained in question link.
#### Time Complexity: 
O(nloglogn)
#### Space Complexity:
O(n)
#### Source code:
```
public int countPrimes(int n) {
   boolean[] isPrime = new boolean[n];
   for (int i = 2; i < n; i++) {
      isPrime[i] = true;
   }
   			// Loop's ending condition is i * i < n instead of i < sqrt(n)
   			// to avoid repeatedly calling an expensive function sqrt().
   for (int i = 2; i * i < n; i++) {
      if (!isPrime[i]) continue;
      
   			//begin from i*i since former prime has map off p(p+k) containing
   			// the not-prime before the i.  
      for (int j = i * i; j < n; j += i) {
         isPrime[j] = false;
      }
   }
   int count = 0;
   for (int i = 2; i < n; i++) {
      if (isPrime[i]) count++;
   }
   return count;
}

```
### Solution 2 Hashmap(however TLE)
#### Idea:
When find a prime less than given n, store it in hashmap,and judge the next prime
by the found former primes in the hashmap.
#### Time Complexity: 
O(nlogn)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    Map<Integer,Integer> prime=new HashMap<Integer,Integer>();
    public int countPrimes(int n) {
        prime.put(2,2);
	    for(int i=2;i<n;i++)
	    isPrime(i,prime);
	    return prime.size();
	}
				   
	void isPrime(int i,Map<Integer,Integer> prime){
		for(int k:prime.keySet()){
    		if(i%k==0) return ;
		}
		if(i>2) if(!prime.containsKey(i)) prime.put(i,i);
	
    }
}
```
#### Reference:

---

