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
#time O(nlog(n)) space O(n) (extra copy of array required if not merging in place)
#merge sort is stable

def merge_sort(array A, start index i, end index j):
  if j <= i+1:
    return
  mid = (i + j) / 2
  merge_sort(A, i, mid)
  merge_sort(A, mid, j)
  B = empty array of size len(A)
  i1,i2,i3 = i,mid,0
  while i1<mid and i2<j:
    if A[i1] <= A[i2]:
      B[i3++] = A[i1++]
    else:
      B[i3++] = A[i2++]
  while i1 < mid:
    B[i3++] = A[i1++]
  while i2 < j:
    B[i3++] = A[i2++]
  i1,i2=i,0
  while i2 < len(B):
    A[i1++] = B[i2++]
```


#### Quick


#### Randomized Quick


#### Counting


#### Radix


#### File



---

### Sort a linked list
