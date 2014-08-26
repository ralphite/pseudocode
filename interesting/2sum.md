### 2 sum

> Q: given an int `sum` and a sorted int array `A` find element `a` and `b`
so that `a+b==sum`. return indices of `a` and `b` (a <= b)

```py
# 2 for loops O(n^2)

def two_sum(A, sum):
  for i in range(len(A)):
    for j in range(i+1, len(A)):
      if A[i]+A[j] == sum:
        return (i,j)
  return (-1,-1)
```

```java
// 1 for loop with binary search O(nlog(n))
import java.util.Arrays;

public int[] twoSum(int[] A, int sum) {
  for(int i = 0; i < A.length - 1; i++) {
    int index = Arrays.binarySearch(A, i+1, A.length, sum-A[i]);
    if(index >= 0) return new int[]{i, index};
  }
  return new int[]{-1, -1};
}
```

```pseudocode
# simplist and most efficient way O(n)

2sum(array A, sum):
  i,j = 0,len(A)-1
  while i < j:
    if A[i]+A[j] < sum:
      i++
    else if A[i]+A[j] > sum:
      j--
    else:
      # assert A[i]+A[j]==sum
      return (i,j)
  return (-1,-1)

'''proof
say a and b exists in A[i..j](inclusive both ends), consider the following cases
case 1) if A[i]+A[j] < sum, then A[i] cannot be a so a and b must exist in A[i+1..j]
case 2) if A[i]+A[j] > sum, then A[j] cannot be b so a and b must exist in A[i..j+1]
'''
```

> Q: what if `A` is not sorted?
>
> the naive 2-loop method still stands. we can quicksort the array then use the
> loop-once and bin-search method which guarantees O(nlog(n)) running time
>
> the best way is to use a hashmap

```java

import java.util.HashMap;

public int[] twoSum(int[] A, int sum) {
  HashMap<Integer,Integer> map = new HashMap<Integer,Integer>((int)(A.length/0.75)+1, 0.75f);
  for(int i = 0; i < A.length; i++) {
    int diff = sum - A[i];
    if(map.containsKey(diff)) return new int[] {map.get(diff), i};
    else map.put(A[i], i);
  }
  return new int[] {-1, -1};
}
```
