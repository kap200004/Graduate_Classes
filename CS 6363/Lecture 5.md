# Dynamic Programming: Fibonacci Numbers and Rod Cutting
## Fibonacci Numbers
- They are recursively defined: $F_{0}=0, F_{1}=1, F_{n}=F_{n-1}+F_{n-2}$ for $n\geq 2$
- We can write a recursive algorithm: 
```
Fibo(n):
	if n <2:
		return n
	else:
		return Fibo(n-1)+Fibo(n-2)
```
- We can solve to get the runtime which is $\Theta(\phi^{n})$. So, the runtime is exponentially large in $n$. This algorithm will not work past a small constant value of $n$. 
- The problem: this algorithm recomputes the same recursive call many times. In fact we can prove through induction that $F_{n-i }$ is compute exponentially many times as function of $i$. 
- The basic idea of dynamic programming is to not make repeated recursive calls. We use a technique known as memoization. 
- We realize that we are making many multiple duplicate recursive calls, so we save recursive computations in a table, and reference that table when a repeated recursive call is made. 
## Dynamic Programming Steps
- Solve the problem recursively. 
- If some recursive callas are made many times, store in a table. 
	- Memoization- put a conditional in your recursive calls. 
	- Dynamic Programming- use a for loop, and go in reverse order of how you made your recursive calls. 
- Can determine the runtime from the recursive code: You just look at the size of the table you need and multiply it by the time it takes to fill in each entry. 
## Space Efficiency
- To compute $F[i]$, iterFibo only needed to know the previous two terms, thus we can modify the algorithm to use only constant space. 
```
IterFibo2(n):
	prev = 1
	cur = 0
	for i to n: 
		next = cur + prev
		prev = cur
		cur = next
	return cur
```
- Cur starts at 0 because if $n=0$ the for loop will not execute and cur will be returned as 0, as it should. 
- Because our model of computation states that multiplications are constant time, for sufficiently large numbers, we can not consider this to be true. For sufficiently large numbers, $n$ additions are $\Theta(n)$ and multiplications are $n\log n$. 
## Rod Cutting
- Given steel rod of length $n$, and we are also given a lookup table $P[1..n]$, where $P[i]$ is the market price for a rod of length $i$. We can cut to any integer length, and cuts are free. How do we maximize the profit? 
- If leftmost cut at $i$, you get $P[i]$ for leftmost piece, and then optimally sell $n-i$ length rod. 
```
cutrod(n):
	if n=0 then
		return 0
	q = 0
	for i = 1 to n do
		q = max(q, P[i], cutrod(n-i))
	return q
```
```
cutRodMem(n): 
	if n=0 then 
		return 0
	if R[n] undefined then
		q =0
		for i=1 to n do 
			q = max{q, P[i]+memcutrod(n-i)}
		R[n] = q
	return R[n]
```
```
DPCutROd(n):
	let R[, ..., n] be an array
	R[0]=0
	for j=1 to n do:
		q=0
		for i=1 to j do: 
			q = max{q, P[i]+R[j-i]}
		R[j] = q
	return R[n]
```

## Dynamic Programming: LIS, LCS, and Edit Distance
### Longest Increasing Subsequence
- We have an array $A$ of n integers. What we want is the longest increasing subsequence in $A$, with this, all subsequent integers are increasing. 
- Subarray means contiguous, subsequence does not have to be contiguous.
- We are really only going to try and compute the length of the longest increasing subsequence. 
- What is a subsequence of $A[1, \dots,n]$?
	- if $N=0$ only subsequence is the empty one, a length of 0. 
	- Otherwise, a subsequence of $A[1, \dots n]$ is either $A[2, \dots, n]$ or $A[1]$ followed by $A[2, \dots, n]$. 
- Recursive Strategy:
	- if the array is empty, return 0. 
	- Otherwise, figure out what to do with $A[1]$ and let the recursion fairy take care of $A[2, \dots, n]$. 
- Strategy: Instead define LIS problem with all elements greater than some value. 
- Let LIS(prev, start) be the LIS in $A[star t, \dots, n]$
```
def LIS(prev, start):
	if start > n then 
		return 0
	ignore = LIS(prev, start+1)
	best = ignore
	if A[start] > A[prev] then 
		include = 1+LIS(start, start+1)
		if include > ignore then
			best = include
	return best
```

### Longest Common Subsequence
- We have two character arrays as input, one of size n, and another of size m. 
- We want to find the length of the longest common subsequence. 
- 