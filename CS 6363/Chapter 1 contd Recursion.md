- There are three common cases where the level-by-level series ($\sum$) is especially easy to evaluate: 
	- Decreasing: If the series decays *exponentially*- ever term is a constant factor smaller than the previous term- then $T(N)=O(f(n))$. In this case the sum is dominated by the value at the root of the recursion tree. 
	- Equal: If all terms in the series are equal, we immediately have $T(n)=O(f(n)*\log_{c}n)$. 
	- Increasing: If the series grows exponentially- every term is a constant factor larger than the previous term- then $T(n)=O(n^{\log _{c}r})$. In this case, the sum is dominated by the number of leaves in the recursion tree. 
## Linear-Time Selection
- The selection problem: Select the $k$th smallest element in an $n$-element array, given the arrand and the integer $k$ as input. 
- We call the algorithm for solving the selection problem quickselect, or one-armed quicksort. 
### Quickselect
- The generic quickselect algorithm chooses a pivot element, partitions the array using the same Partition subroutine as QuickSort, and then recursively searches only one of the two subarrays, specifically, the one that contains the $k$th smallest element of the original input array. 

```pseudo
QuickSelect(A[1..n], k):
	if n=1:
		return A[1]
	else:
		choose a pivot element A[p]
		r <- Partition(A[1...n], p)
		if k<r:
			return QuickSelect(A[1..r-1], k)
		if k > r:
			return QuickeSelect(A[r+1..n], k-r)
		else:
			return A[r]
```

- Note that also with quick select, if the chosen pivot element is always either the smallest or largest element in the array, the recurrence simplifies to $T(n)=T(n-1)+O(n)$ which implies that $T(n)=O(n^2)$. 
### Good Pivots
- We could avoid the quadratic worst-case behavior in quickselect and quicksort if we could somehow magically choose a good pivot. 
- In other words, if we could somehow quickly find an element that's even close to the median in linear time, we could find the exact median in linear time. 
- MomSelect chooses a good quickselect pivot by recursively computing the median of a carefully-choses subset of the input array. 
- Specifically, we divide the input array into $\lceil\frac{n}{5} \rceil$ blocks, each containing exactly 5 elements, except possibly the last which we can fill with infinities. 
- We compute the median of each block by brute force and collect those medians into a new array $M\left[ 1\dots \lceil \frac{n}{5} \right \rceil]$, and then recursively compute the median of this new array. Finally, we use the median of the block medians, called mom, as the quickselect pivot:

```pseudo
MomSelect(A[1..n], k):
	if n <= 25: 
		use bruteforce
	else:
		m = ceil(n/5)
		for i in range(m):
			M[i] = medianOfFive(A[5i-4...5i])
		mom = MomSelect(M[1...m], m/2)
		r = Partition(A[1,.., n], mom)
		if k<r:
			return MomSelect(A[1..r-1], k)
		if k>r:
			return MomSelect(A[r+1..n], k-r)
		else: 
			return mom
```

