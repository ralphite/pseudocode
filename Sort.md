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

#high level work flow
1) deal with base case
2) recursively merge sort left half and right half
3) merge sorted left half and sorted right half into a new array
4) copy sorted new array back

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

```
#partition array around a pivot element so that elements on the 
#left are smaller and elements on the right are larger than the 
#pivot element

#quick sort is an unstable in-place sorting algorithm

#high level work flow
1) deal with base case
1) choose pivot element p and move it to the end
3) partition around p
4) recursively sort both sides (no combine/merge required)

def quick_sort(array A, start index l, end index r):
  if r <= l+1:
    return
  
  p = index of chosen pivot (l <= p < r)
  swap A[p], A[r-1]
  
  i,j = l,l
  while j < r-1:
    if A[j] < A[r-1]:
      swap A[i], A[j]
      i++
    j++
  swap A[i], A[r-1]
  
  quick_sort(A, l, i)
  quick_sort(A, i+1, r)
```

#### Heap sort


#### Counting

```
# sort many small integers
# not a comparison based sort, often used in radix sort
# running time is O(n+k) ([0,k) is the range of elements in A)

def count_sort(array A):
  count_table = [] of length k
  for elem in A:
    count_table[elem]++
  
  j = 0
  for i in [0, len(count_table)):
    do count_table[i] times:
      A[j++] = i
```


#### Radix

```
# useful when the number of digits of each of the input elements
# is small.

# workflow
say all numbers have at most k digits
for i in [1..k]:
  sort the input based on the ith least significant digit, any stable
  sort method will do, usually count sort is used

# time O(n*k) space O(n)
# k is Omega(log(n))

def radix_sort(array A, number of digits k):
  for i in [1..k]:
    B = array of 10 lists
    for a in A:
      d=(a%(10^i))/(10^(i-1)) # ith digit from left to right
      B[d].add(a)
    j=0
    for i in [0..9]:
      for e in B[i]:
        A[j++]=e
```

#### Bucket


#### Shell


#### File



---

### Relevant questions

#### Sort a linked list (**bottom up merge sort**)

```
#Insertion sort time O(n^2) space O(1)
#Top down merge sort time O(nlog(n)) space O(log(n))
#Bottom up merge sort time O(nlog(n)) space O(1)

#High level workflow:
get length of list len
for k in (1,2,4,8,...) where k<=len:
  split list into segments of length k
  merge adjacent two segments


def bottom_up_mergesort_linkedlist(node head):
  len = length of linkedlist
  
  dummy head dm
  for seg_len=1; seg_len<=len; seg_len*=2:
    dm.next=null
    cursor c=dm
    
    cursors c1,c2,c3=head,head,null
    while c1 != null:
      c3=null # so that we can quit from while loop when the end is reached
      for i=0; i<seg_len-1; i++:
        if c2!=null:
          c2=c2.next
        else:
          break
      if c2!=null:
        tmp=c2
        c2=c2.next
        tmp.next=null
        c3=c2
        for i=0; i<seg_len-1; i++:
          if c3!=null:
            c3=c3.next
          else:
            break
        if c3!=null:
          tmp=c3
          c3=c3.next
          tmp.next=null
          
      while c1!=null && c2!=null:
        if c1.val<=c2.val:
          c.next=c1
          c1=c1.next
          c=c.next
        else:
          c.next=c2
          c2=c2.next
          c=c.next
      while c1!=null:
        c.next=c1
        c1=c1.next
        c=c.next
      while c2!=null:
        c.next=c2
        c2=c2.next
        c=c.next
        
      c1,c2=c3,c3
      
    head=dm.next
    
  return dm.next
```


#### Counting invertions

```
#Similar to merge sort
#Sort while counting the split inversions

def sort_and_count(array A, start index i, end index j):
  if j - i <= 1:
    return 0

  mid = (j - i) / 2
  left_inversions = sort_and_count(A, i, mid)
  right_inversions = sort_and_count(A, mid, j)

  B = empty array of length j - i
  i1,i2,i3,split_inversions = i,mid,0,0
  while i1 < mid and i2 < j:
    if A[i1] <= A[i2]:
      B[i3++] = A[i1++]
    else:
      split_inversions += mid-i1
      B[i3++] = A[i2++]
  while i1 < mid:
    B[i3++] = A[i1++]
  while i2 < j:
    B[i3++] = A[i2++]

  i1,i3=i,0
  while i3 < len(B):
    A[i1++] = B[i3++]

  return left_inversions + right_inversions + split_inversions
```

#### Sort iteratively


#### Prove lower bound of comparison based sort is Omega(nlog(n))
