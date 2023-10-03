# Optimal Binary Search Trees and Dynamic Programming in Trees
- Given a sorted array of $A[1\dots n]$ of keys, a binary search tree for $A$ is a binary tree such that each node stores a unique key from $A$, and for any node $v$ all keys  in left/right subtree are smaller/larger than key at $v$. 
- Cost of accessing key is its path length from root, i.e. depth. 
- There are many possible binary search tree for $A$. 
- Suppose we are also given a frequency table that tells us the distribution of element access. 
- Choose a search tree that minimizes the total access cost. 
- Let $d(i,T)$ be the depth of $A[i]$ in tree $T$. The total access cost is $\sum F[i]d(i,T)$. 
- Intuitively, higher frequency should be closer to the root, but the most frequent may not be at the root. 
- The optimal tree also may not be a full binary tree. 
- Observe that since $T$ is a valid search tree, and $A$ is sorted, left(T) contains $A[1\dots r-1]$ and right(T) contains $A[r+1, \dots n]$. 

## Dynamic Programming in Trees
- Dynamic programming not only works for arrays, but also for trees, using post order traversal. 
- 