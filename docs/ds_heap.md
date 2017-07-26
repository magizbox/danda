## Heaps

A heap is just what it sounds like —  a pile of values organized into a binary tree-like structure adhering to some ordering property. When we add elements to a heap, we fill this tree-like structure from left to right, level by level. This makes heaps really easy to implement in an array, where the value for some index ii's left child is located at index \( 2i+1 \) and the value for its right child is at index \( 2i+2 \) (using zero-indexing). Here are the two most fundamental heap operations:

* *add*: Insert an element into the heap. You may also see this referred to as push.
* *poll*: Retrieve and remove the root element of the heap. You may also see this referred to as pop.

### Max Heap

This type heap orders the maximum value at the root.

When we *add* the values \( 1→2→3→4 \) to a Max heap, it looks like this:

![](https://s3.amazonaws.com/hr-challenge-images/24110/1474683435-0fd86b37ef-minheap-add.png)

When we *poll* the same Max heap until it's empty, it looks like this:

![](https://s3.amazonaws.com/hr-challenge-images/24110/1474682804-9cef903049-maxheap-poll.png)

### Min Heap

This type of heap orders the minimum value at the root.

When we *add* the values \( 1→2→3→4 \) to a Min heap, it looks like this:
 
![](https://s3.amazonaws.com/hr-challenge-images/24110/1474683435-0fd86b37ef-minheap-add.png) 

When we *poll* the same Min heap until it's empty, it looks like this:
 
![](https://s3.amazonaws.com/hr-challenge-images/24110/1474683444-23a807baaa-minheap-poll.png) 

## Applications

The heap data structure has many applications.

* *Heapsort*: One of the best sorting methods being in-place and with no quadratic worst-case scenarios.
* *Selection algorithms*: A heap allows access to the min or max element in constant time, and other selections (such as median or kth-element) can be done in sub-linear time on data that is in a heap.
* *Graph algorithms*: By using heaps as internal traversal data structures, run time will be reduced by polynomial order. Examples of such problems are Prim's minimal-spanning-tree algorithm and Dijkstra's shortest-path algorithm.
* *Priority Queue*: A priority queue is an abstract concept like "a list" or "a map"; just as a list can be implemented with a linked list or an array, a priority queue can be implemented with a heap or a variety of other methods.
* *Order statistics*: The Heap data structure can be used to efficiently find the kth smallest (or largest) element in an array.

## Challenges

* ["Heaps: Find the Running Median". *hackerrank*. 2016](https://www.hackerrank.com/challenges/ctci-find-the-running-median)

## References

* ["Heaps". *AllisonP, hackerrank*. 2016](https://www.hackerrank.com/topics/heaps)
* ["Heap (data structure)". *wikipedia*. 2016](https://en.wikipedia.org/wiki/Heap_(data_structure)#Applications)
