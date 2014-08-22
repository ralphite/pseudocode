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
      if(A[j+1]<A[j]):
        swap A[j+1], A[j]
      else:
        break
```


#### Merge


#### Quick


#### Randomized Quick


#### Counting


#### Radix


#### File



---

### Sort a linked list
