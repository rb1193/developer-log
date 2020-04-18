# Stacks and Queues

## Stacks

Two basic implementations of stacks are commonplace in Java. One is using a linked list, which is simple but slightly slow for very large queues as it requires a few operations to perform pops and pushes. The other is an array based implementation, which is faster as pop and push operations are direct accesses to the array but needs to handle underflow and overflow errors and take care to remove references to items which have been popped from the stack.

Overflow errors on array based stacks can be handled by doubling the size of the array every time the stack becomes full. To prevent wasted memory when lots of items are popped from the stack, the array should be halved in size when it is one quarter full. One quarter is used rather than a half to prevent frequent resizes when a sequence of pops and pushes occurs on a stack at the size of a power of two.

Linked list based stacks take up more memory because each item is stored as an object. The operations are slightly slower too, though still in constant time. If all operations must happen in exactly the same time, a linked list is the way to go. If you don't mind some operations taking N time, then an array is the better choice. Arrays still take an amortized constant time, but operations requiring a resize take N time.

The preferred Java stack implementation is the `Array Deque` structure. `java.util.Stack` is considered a legacy structure.

## Queues

Queues can also be implemented using either linked lists or arrays. The tradeoffs you make are broadly similar as they are for stacks.

## Gotchas

- Linked lists are not an efficient way of accessing a particular item, even though it's possible with many implementations, because you have to potentially iterate through the whole list.
