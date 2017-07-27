# Insertion Sort

This is an in-place comparison-based sorting algorithm. Here, a sub-list is maintained which is always sorted. For example, the lower part of an array is maintained to be sorted. An element which is to be 'insert'ed in this sorted sub-list, has to find its appropriate place and then it has to be inserted there. Hence the name, **insertion sort**.

The array is searched sequentially and unsorted items are moved and inserted into the sorted sub-list (in the same array). This algorithm is not suitable for large data sets as its average and worst case complexity are of Ο(n2), where n is the number of items.

# How Insertion Sort Works?

We take an unsorted array for our example.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/unsorted_array.jpg)

Insertion sort compares the first two elements.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_1.jpg)

It finds that both 14 and 33 are already in ascending order. For now, 14 is in sorted sub-list.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_2.jpg)

Insertion sort moves ahead and compares 33 with 27.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_3.jpg)

And finds that 33 is not in the correct position.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_4.jpg)

It swaps 33 with 27. It also checks with all the elements of sorted sub-list. Here we see that the sorted sub-list has only one element 14, and 27 is greater than 14. Hence, the sorted sub-list remains sorted after swapping.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_5.jpg)

By now we have 14 and 27 in the sorted sub-list. Next, it compares 33 with 10.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_6.jpg)

These values are not in a sorted order.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_7.jpg)

So we swap them.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_8.jpg)

However, swapping makes 27 and 10 unsorted.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_9.jpg)

Hence, we swap them too.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_10.jpg)

Again we find 14 and 10 in an unsorted order.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_11.jpg)

We swap them again. By the end of third iteration, we have a sorted sub-list of 4 items.

![](https://www.tutorialspoint.com/data_structures_algorithms/images/insertion_sort_12.jpg)

This process goes on until all the unsorted values are covered in a sorted sub-list. Now we shall see some programming aspects of insertion sort.

# Algorithm

Now we have a bigger picture of how this sorting technique works, so we can derive simple steps by which we can achieve insertion sort.

```
Step 1 − If it is the first element, it is already sorted. return 1;
Step 2 − Pick next element
Step 3 − Compare with all elements in the sorted sub-list
Step 4 − Shift all the elements in the sorted sub-list that is greater than the 
         value to be sorted
Step 5 − Insert the value
Step 6 − Repeat until list is sorted
```

# Pseudocode

```
procedure insertionSort( A : array of items )
   int holePosition
   int valueToInsert
	
   for i = 1 to length(A) inclusive do:
	
      /* select value to be inserted */
      valueToInsert = A[i]
      holePosition = i
      
      /*locate hole position for the element to be inserted */
		
      while holePosition > 0 and A[holePosition-1] > valueToInsert do:
         A[holePosition] = A[holePosition-1]
         holePosition = holePosition -1
      end while
		
      /* insert the number at hole position */
      A[holePosition] = valueToInsert
      
   end for
	
end procedure
```


