# Recursion
## Reductions
- Reducing one problem $X$ to another problem $Y$ means to write an algorithm for $X$ that uses an algorithm for $Y$ as a black box or subroutine. 
- Crucially, the correctness of the resulting algorithm for $X$ cannot depend in any way on how the algorithm for $Y$ works. 
- It's often best to literally think of the black box as functioning purely by magic, its implementation is not important to think about. 
- Even when you do know precisely how your components work, it is often extremely helpful to pretend that you do not. 
## Simplify and Delegate
- Recursion is a particularly powerful kind of reduction, which can be described loosely as follows: 
	- If the given instance of the problem can be solved directly, solve it directly. 
	- Otherwise, reduce it to one or more simpler instances of the same problem. 
- It may be helpful to imagine that someone else is going to solve the simpler problems. 
- Your only task is to simplify the original problem, or to solve it directly when simplification is either unnecessary or impossible. 
- Eventually the recursive reductions must lead to an elementary base case that can be solved by some other method. 
- The most common way to satisfy this condition is to reduce to one or more smaller instances of the same problem.
## Tower of Hanoi
- The problem: How can we move a tower of $n$ disks from one peg to another, using a third spare peg as an occasional placeholder, without ever placing a disk on top of a smaller disk?
- Instead of trying to solve the entire puzzle at one, we should concentrate on moving just the largest disk. We can't move it at the beginning because all the other disks are in the way. So first we have to move those $n-1$ smaller disks to the spare peg. 
- Finally, to finish the puzzle, we have to move the $n-1$ smaller disks from the spare peg to their final destination. 
- We have to stop here as we are done, we have successfully reduced the n-disk Tower of Hanoi problem to two instances of the $n-1$-disk Tower of Hanoi problem, which we can hand off to recursion to carry out. 
- It may be tempting to think about how all those smaller disks move around- or more generally, what happens when the recursion is unrolled, but we really should not do that. 
- For most recursive algorithms, unrolling the recursion is neither necessary or helpful. Our only task is to reduce the problem instance we're given to one or move simpler instances, or to solve the problem directly if a reduction is impossible. 
```pseudo
Hanoi(n, src, dest, temp):
	if n >0:
		Hanoi(n-1, src, temp, dest)
		move disk n from src to dest
		Hanoi(n-1, temp, dest, src)
```
## Quicksort
- Compared to mergesort, in this algorithm, the hard work is splitting the array into smaller subarrays ***before*** recursion, so that merging the sorted subarrays is trivial. 
- The algorithm: 
	- Choose a pivot element from the array. 
	- Partition the array into three subarrays containing the elements smaller than the pivot, the pivot element itself, and the elements larger than the pivot. 
	- Recursively quick sort the first and last subarrays. 
- In the partition subroutine, the input parameter $p$ is the index of the pivot element in the unsorted array; the subroutine partitions the array and returns the new index of the pivot element. 
- The variable $l$ counts the number of items in the array that are less than the pivot element. 
```psuedo
Quicksort(A[1...n]):
	choose a pivot element A[p]
	r <- Partition(A, p)
	QuickSort(A[1...r-1])
	QuickSort(A[r+1...n])

Partition(A[1...n], p)
	swap A[p] <-> A[n]
	l = 0
	for i=1 in range(1, n-1):
		if A[i]<A[n]:
		l = l+1
		swap A[l] <-> A[]
	swap A[n] <-> A[l+1]
	return l+1
```
- To prove partition is correct, we need to prove the following loop invariant: At the end of each iteration of the main loop, everything in the subarray $A[1\dots l]$ is less than $A[n]$, and nothing in the subarray $A[l+1\dots n]$ is less than $A[n]$. 
- For quicksort, we get a recurrence that depends on $r$, the *rank* of the pivot element: $T(n) = T(r-1)+T(n-r)+O(n)$. 
- If we could somehow always magically choose the pivot to e the median element of the array $A$, the two subproblems would be as close to the same size as possible, and the recurrence would become $T(n)=2T\left( \frac{n}{2} \right)+O(n)$. 
- In the worst case, the two subproblems are completely unbalanced, either $r=1$ or $r=n$ and the solution is $T(n)=T(n-1)+O(n) = O(n^2)$.
## The Pattern 
- Both mergesort and quick sort follow a general three-step pattern called divide and conquer: 
	- Divide the given instance of the problem into several independent smaller instances of ***exactly*** the same problem. 
	- Delegate each smaller instance to recursion. 
	- Combine the solutions for the smaller instances into the final solution for the given instance. 
- If the size of any instance falls below some constant threshold, we abandon recursion and solve the problem directly, by brute force, in constant time. 
## Recursion Trees
- Recursion trees are a simple, general, pictorial tool for solving divide-and-conquer recurrences. 
- A recursion tree is a rooted tree with one node for each recursive subproblem. 
- The value of each node is the amount of time spent on the corresponding subproblem excluding recursive calls. 
- Thus, the overall running time of the algorithm is the sum of the values of all nodes in the tree. 
- Imagine a divide-and-conquer algorithm that spends $O(f(n))$ time on non-recursive work, and then makes $r$ recursive calls, each on a problem of size $\frac{n}{c}$. The running time of this algorithm is governed by the recurrence $T(n)=rT\left( \frac{n}{c} \right)+f(n)$. 
- The root of the recursion tree for $T(n)$ has value $f(n)$ and $r$ children, each of which is the root of a recursively defined recursion tree for $T\left( \frac{n}{c} \right)$. 
- Equivalently, a recursion tree is a complete $r-ary$ tree where each node at depth $d$contains the value $f\left( \frac{n}{c^{d}} \right)$. Feel free to assume that $n$ is an integer power of $c$, so that $\frac{n}{c^d}$ is always an integer, although in fact this doesn't matter. 
- The leaves of the recursion tree correspond to the base case(s) of the recurrence.
- For each integer $i$, the $i$th level of the tree has exactly $r^{i}$ nodes, each with a value of $f\left(  \frac{n}{c^i} \right)$. Thus, $T(n)=\sum^{L}_{i=0}r^if\left(  \frac{n}{c^i} \right)$ where $L$ is the depth of the tree
- Our base case $n_{0}=1$ immediately implies that $L=\log_{c}n$ because $\frac{n}{c^L}=n_{0}=1$. 
- It follows that the number of leaves in the recursion tree is exactly $r^L=r^{\log_{c}n}=n^{\log_{c}r}$. 