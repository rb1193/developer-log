# Priority Queues

Priority queues are a data structure that is similar to a queue but the equivalent of the pop operation removes either the largest or smallest item in the queue. Elementary priority queues may be backed by an ordered or unordered data structure, depending on whether reads or writes are the more common operation, but both require N times for either insert or pop operations so they're not very useful.

## Applications

Wide range of applications. Event simulation, statistical analysis, graph traversal, to name but a few.

## Binary Heap

Elementary priority queues can be useful when the size of the queue is very small, but for most practical implementations a binary heap-based implementation provides better performance (log(N)).

The binary heap is a binary tree where no node is a larger value than its parent node (or smaller if we want to implement a minimum-based priority queue). Internally, the tree is stored in an array where the top value is stored in position 1 (because we rely on dividing/multiplying by 2 to find positions of parents/children). When a new node is added to the heap, if it is larger than its parent, it is exchanged with its parent recursively until it is smaller than its parent.

Insertion occurs in 1 + log(N) in the worst case.

Values may be changed in place, in that case we recursively exchange the node with its largest child (if the new value is smaller than the largest child).

Popping the largest item is as simple as removing the top node from the tree. However, we then need to restore the tree, so we move the bottom node to the top of the tree and exchange it downwards until it is in the correct position. This takes at most 2log(N) compares.

## Heapsort

To perform a heap sort, we put the items into a binary heap first, then sort by removing the max/min item until the heap is empty.

Heapsort runs in worst case `Nlog(N)` time and sorts in place. However it is not stable and each iteration takes a bit longer than quicksort, so it isn't used very often. Heapsort also makes poor use of cached memory for large data sets because parents and children will be stored a long way away from each other in memory location terms.
