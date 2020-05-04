# Sorting

## Performance

- Selection Sort: Running time insensitive to input. Runs at `~n^2 / 2`. Makes exactly `n` exchanges.
- Insertion Sort: Running time is sensitive to input. Makes `~1/4n^2` comparisons and `~1/4n^2` exchanges. Worst case is `n-1` compares, 0 exchanges. Worst is `n^2/2` compares and `n^2/2` exchanges. Insertion sort is fast (linear time) for partially sorted arrays, making it a better choice than mergesort.
- Shellsort: Run insertion sort using gradually decreasing "stride length" values. Increments of `3x + 1` work pretty well. Worst case running time using `3x + 1` increments is `O(N^(3/2)). Real case is usually quite a bit better.
- Mergesort: Runs in `Nlog(N)`. This is optimal for sorting. Uses memory equal to 2N so we may find that in embedded systems insertion/shell sort can be a more practical choice. Mergesort can be further optimised by using an insertion sort once the sub-arrays get down to ~ 7 values.
- Quicksort: Uses only N memory. Generally, quicksort is faster than mergesort as the average case is better. In the worst case it runs in quadratic time (when the initial shuffle happens to put the array in exactly the right order - highly unlikely). Optimise by using insertion sort for partitions of ~ 10 values.
- 3-way Quicksort: This is preferable to quicksort when the array has many duplicate keys, although it still performs well when it does not. It can reduce sorting time to linear in many applications where duplicate keys are prevalent.
- Heapsort: Also runs in `Nlog(N)` in the worst case, but sorts in place so little memory overhead.

## Implementation

- Selection Sort: Select the next-least item from the remaining unsorted items as you iterate through the collection.
- Insertion Sort: Insert the next item in the right place in the sorted items as you iterate through the collection.
- Shell Sort: Same as insertion sort, but iterate through the collection using gradually decreasing values of `h` as the stride length.
- Mergesort: Recursively divide the collection into two, sort the two halves, and merge back together.
- Mergesort (bottom-up): Divide the collection into collections of length 2, sort and merge to create collections of length 4, until whole collection is sorted.
- Quicksort: Shuffle items. Find an item `j` that is in the correct position (only lesser items to the left, only greater items to the right). Recursively sort the two partitions either side of `j`.
- 3-way Quicksort: Shuffle items. Make `j` the first item. Partition the items 3 ways: < `j`, = `j` and `j`. Recurse through the partitions as necessary.
- Heapsort: See [priority queues](/Priority_Queues.md)

## Stability

When sorting by multiple keys, it is often useful to maintain the order from the first key when the keys match sorting by the second key. A sort is stable when objects with keys of equal value can not move past each other during sorting.

### Stable sorts

- Insertion sort
- Mergesort

### Unstable sorts

- Selection sort
- Shellsort
- Quicksort
- Heapsort

## Applications

- Insertion sort is good for partially sorted arrays.
- Shellsort is fast unless the array is massive, and is frequently used in embedded programming because very little code is required and sorting is performed in place.
- Mergesort is good for general purpose sorting where memory restrictions are not an issue.

### Shuffling

Shuffling can be performed by iterating through the array, generating a random number between 0 and `i` (inclusive), and swapping the positions of elements corresponding to `i` and the random number.

### Convex Hull

Requires two sorts. One to find the lowest point on the y-axis, one to organise the other points in relation to the lowest point depending on their polar angle.

### Selection

Select the kth largest item from a set of items. Use quicksort-like partitioning but only sort the partition that the kth value is in. Takes linear time on average.
