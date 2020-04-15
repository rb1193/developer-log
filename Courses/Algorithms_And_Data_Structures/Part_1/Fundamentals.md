# Fundamentals

## Devising Algorithms

How do we identify a useful algorithm?

1. Model the problem
2. Find an algorithm to solve the problem
3. Check if the algorithm performs acceptably and fits within available memory
4. Identify why algorithms does not perform acceptably or fit within memory
5. Address the problem
6. Repeat steps 3-5 until satisfied

## Union Find

The union find algorithm is useful for working out whether two nodes in a network are connected. It can also be used to work out if there is a path from the top to the bottom of an object by providing an extra "virtual" node at each end of the network. You can also invert it to work out which connections remain in a network as connections are removed. The data structure is based around an internal forest of tree structures, starting with each node as its own tree, and two methods:

### Union

```(java)
public void union(int p, int q) {}
```

The union method joins two nodes via an edge. Under the hood, what happens is that the root of tree `p` is placed underneath the root of tree `q`. To make this more efficient, the smaller tree is placed underneath the larger tree, which ensures that the minimum number of traversals is required to reach the root from any given node. Path compression should also be applied at this stage (essentially flattening the tree so all nodes in the union path point directly to the node).

### Connected

```(java)
public boolean connected(int p, int q) {}
```

The connected method checks whether or not the roots of the two nodes match. If they do, the nodes are connected.

### Complexity

A good union find data structure runs both the `union` and `connected` methods in O(n log(n)) time. They are logarithmic functions. Logarithmic functions are very powerful because as the size of `n` doubles, the function takes only half as much time again to run. This essentially means, given the rough constant that a CPU can traverse approximately 1,000,000 bits of memory per second, that logarithmic functions take a maximum of five seconds to run even for truly enormous data sets.
