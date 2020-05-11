# Symbol Tables

"Symbol table" is a generic term for a key-value storage structure.

The most basic implementations of symbol tables are using a linked list (for unordered keys) or two arrays (one for keys, one for values) for keys that have a total order. Both of these are pretty slow though. The two arrays solution is fast enough when there are lots of reads and very few writes because binary search can be used to look up the value for a key.

## Binary Search Trees

A better implementation could use a BST, a binary tree in symmetric order. For a binary tree to be in symmetric order, each node must have a key and every node's key is larger than all of the keys in its left subtree and smaller than all the keys in its right subtree.

### BST Performance

BSTs achieve both insertion and search in an average of logarithmic time, but tree shape depends on the order of insertion. Worst case can be `N` for search and insertion, but it's highly unlikely. Mathematically its attributes correspond with quicksort. However, unlike quicksort, the entire set isn't available to randomize before processing, so average performance cannot be guaranteed.

Deletion using Hibbard's Deletion (see below) evetually causes all operations to run at an average case of sqrt(N).

### BST Implementation

Every node has four attributes: key, value, left_subtree, right_subtree. The subtrees may be null when the node is at the edge of the tree. To search or insert, iterate through the nodes going either left or right until a null node is reached.

In some cases, (e.g. when wanting to find the nth position node) it may be useful for nodes to also have a count attribute which records the number of nodes in its subtree (including itself, the root).

To iterate through a BST, convert the tree into a queue and iterate that.

Deletion is tricky. You can be lazy and set the deleted node's value to null, but leave it there to guide searches, however this doesn't work very well. A better solution is called Hibbard's Deletion, which works as follows:

- If node has no children, set parent's right or left attribute (whichever was used to reach the node) to null.
- If node has one child, replace parent's link to node with the child.
- If the node has two children, find the minimum of the node's right subtree, remove the node from that tree and replace the deleted node with it.

Unfortunately Hibbard's deletion results in an increasingly asymmetric tree, causing performance degradation over numerous deletion operations, and there is no known superior alternative.

## 2-3 Trees

2-3 trees allow one or two keys per node. If a node has two keys it may have up to 3 children. 2-3 trees have perfect balance - every path from a leaf to the root has the same length. The three nodes work as follows:

- to the left: nodes whose keys are smaller than the smaller of the keys in the parent node
- in the middle: nodes whose keys are between the values of the keys in the parent node
- to the right: nodes whose keys are greater than the larger of the keys in the parent node

### 2-3 Tree Performance

2-3 trees guarantee `logN` performance for insertion, deletion and search operations.

### 2-3 Tree Implementation

Search works as for a binary search tree, but insertion is more complex as the tree has to be manipulated to maintain its invariants. If a key is inserted at the position of a two node then it is simply added to that node to create a three node. If the node at the insert position is already a 3 node, create a temporary four node and move the middle value to create a 3 node in the parent (the child nodes will all now be two nodes). Repeat up the tree as necessary.

However, while easy to describe, this is actually pretty difficult to implement in code because of the number of cases that need to be handled depending on whether you're dealing with a 2 or 3 node, whether the new item is smaller, between or larger than the parent keys etc. There are easier implementations that provide similar performance guarantees.

## Red Black Trees

Red black tree essentially represent 2-3 trees as BSTs, which are much easier to implement. They're called red-black trees because BST links between nodes that are really a single 3 node are referred to as "red" links. In a left-leaning red-black tree, the larger node in a 3 node has a red link to its left to the other key in the node.

### Red-Black Tree Performance

Red-black naturally share the performance guarantees of 2-3 trees, but without the cumbersome implementation, making them very useful indeed.

### Red-Black Tree Implementation

Search implmentation is identical to BST searching. Insertion may sometimes require that three nodes are "rotated" either right or left before or after insertion to maintain the balance of the tree.

## B-Trees

B-trees generalize the 2-3 tree by allowing up to M-1 keys per node, where M is the largest amount of data that can be processed at one time (e.g. B-trees are often used in filesystem applications, in this case the value of M might be 1024 if that's the largest number of files that can be shown in an explorer). B-trees are stupidly powerful, they make data sets of billions of items searchable in at most 5 operations.

## Kd Trees

Kd trees (k is the number of dimensions) extend ordered symbol tables to multi-dimensional keys. They're useful for performing operations that deal with points in multi-dimensional geometric space. They work by dividing the search space in two at each point added to the tree. The direction of the division at each level of the tree is orthogonal to the preceding level (e.g. a 3D tree is divided by successive horizontal and vertical planes).

## Hash Tables

Hash tables allow for constant time inserts and reads but don't permit ordered operations, as the hash keys cannot be ordered. Associative arrays from PHP are really hash tables. Hash codes should ideally be unique, though in Java they don't strictly have to be.

When using a 2D array with a lot of empty/zero entries, it may be more efficient to use an array of hash tables to store the data.
