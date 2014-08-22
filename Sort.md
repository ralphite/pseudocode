### Sort a randomly accessible array

#### Bubble

```
#bubble up bigger elements

def bubble_sort(array A):
  for (i=len(A)-1; i>=0; i--):
    for (j=0; j<i; j++):
      if (A[j] > A[j+1]):
        swap A[j], A[j+1]
```


#### Selection

```
#select the smallest left

def selection_sort(array A):
  for (i=0; i<len(A); i++):
    minIndex = i
    for (j=i+1; j<len(A); j++):
      minIndex = j if A[j] < A[minIndex]
    swap A[i], A[minIndex]
```


#### Insertion

```
#insert the unsorted items one by one to the sorted sequence

def insertion_sort(array A):
  for (i=1; i<len(A); i++):
    for(j=i-1; j>=0; j--):
      if(A[j+1] < A[j]):
        swap A[j+1], A[j]
      else:
        break
```


#### Merge

```
#partition and merge
#time O(nlog(n)) space O(nlog(n))

def merge_sort(array A):
  if len(A) <= 1:
    return A
  else:
    A1 = merge_sort(A[0:mid])
    A2 = merge_sort(A[mid:])
    i,i1,i2 = 0,0,0
    while i1<len(A1) and i2<len(A2):
      if A1[i1] <= A2[i2]:
        A[i++] = A1[i1++]
      else:
        A[i++] = A2[i2++]
    while i1 < len(A1):
      A[i++] = A1[i1++]
    while i2 < len(A2):
      A[i++] = A2[i2++]
  return A
```

#### Quick


#### Randomized Quick


#### Counting


#### Radix


#### File



---

### Sort a linked list
