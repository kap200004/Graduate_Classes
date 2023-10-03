## Recursion Trees

### Introduction
- The root node represents the non-recursive part of the function and is denoted by $f(n)$.
- Each level of the tree breaks down the master recurrence equation $T(n) = aT\left( \frac{n}{b} \right) + f(n)$ into $a$ subproblems, each of size $\frac{n}{b}$.

### Number of Levels
- The tree is divided by $b$ at each level. 
- The depth of the tree is $\log_{b} n$ if we reduce the problem size by a constant factor $b$ at each level.

### Number of Leaves
- The number of nodes at each level increases by a factor of $a$.
- The total number of leaves is $a^{\log_{b} n} = n^{\log_{b} a}$.

### Total Work Done
- The sum of all the level sums gives us the total work done.
- This is represented by $\sum_{i=0}^{\log_{b} n} a^{i}f\left( \frac{n}{b^{i}} \right)$.

### Geometric Series Check
- To check whether the sum forms a geometric series, we look at the ratio of successive level sums.
- The ratio is given by $\frac{a^{i+1}f\left( \frac{n}{b^{i+1}} \right)}{a^{i}f\left( \frac{n}{b^{i}} \right)} = a \frac{f\left( \frac{n}{b^{i+1}} \right)}{f\left( \frac{n}{b^{i}} \right)}$.
    - If this ratio is greater than 1, the sum behaves like an increasing geometric series.
    - If it's less than 1, it's a decreasing geometric series.

### Asymptotic Behavior
- In a geometric series, the term with the largest magnitude dominates the sum.
    - For an increasing series, the last term is the largest.
    - For a decreasing series, the first term is the largest.
- If the last level sum is the largest and the base case is $O(1)$, the total work is $n^{\log_{b} a}$.
- If the level sums are constant, the total work is $f(n) \log_{b} n$.

### Closest Pair
- The problem: Given $n$ points $P \subset R^d$, find the closest pair of points. 
- The naive way to solve this problem can be done in $O(dn^2)$, but we can actually solve this problem in $O(n\log n)$ time in constant dimension. 
- We can first consider the one dimensional case: 
	- Assume $P={p_{1}, p_{2}\dots,p_{n}}$ sorted by x-coordinate. 
	- In one dimensional we can actually just find the minimum of all adjacent pairs. 
	- This algorithm does not generalize to higher dimensions, so we can try to divide and conquer:
		- We can split the list of points and make two calls. Conquer: the closest pair of points is either the closes from the left, right, or across the dividing line. 