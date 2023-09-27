# Backtracking
## Subset Sum
- Given a set $X$ of positive integers and a target integer $T$, is there a subset of elements in $X$ that add up to $T$? There can be many such subsets, but we only require to know if there is one, so we will return True or False. 
- There are two trivial cases. If the $T$ is zero, we can immediately return True, because the empty set is a subset of all sets. If $T \neq 0$ and the set is empty or $T$ is negative, we can immediate return false. 
- Consider an arbitrary element $x$ in $X$. There is a subset of $X$ that sums to $T$ if and only if one of the following statements is true: 
	- There is a subset of $X$ that includes $x$ and whose sum is $T$.
		- In this case, there must be a subset of $X$ without $x$ that sums to $T-x$
	- There is a subset of $X$ that excludes $x$ and whose sum is $T$.
		- In this case, there must be a subset of $X$ without $x$ that sums to $T$. 
- We can solve subsetSum(X, T) by reducing to two simpler instances of subsetSum(X-x, T) and subsetSum(X-x, T-x). 
```
subsetSum(X, T):
	if T == 0:
		return True
	if T < 0 or X is empty: 
		return false
	x = X.pop()
	with = subsetSum(X, T-x)
	without = subsetSum(X, T)
	return with or without
```
## The General Pattern
- Backtracking algorithms are commonly used to make a sequence of decisions, with the goal of building a recursively defined structure satisfying certain constraints. 
- In each recursive call to the backtracking algorithm, we need to make exactly one decision, and our choice must be consistent with all previous decisions. 
- Thus, each recursive call requires not only the portion of the input data we have not yet processed, but also a suitable summary of the decisions we have already made.
- When we design new recursive backtracking algorithms, we must figure out in advance what information we will need about past decisions in the middle of the algorithm. If this information is nontrivial, our recursive algorithm might need to solve a more general problem than the one we were originally asked to solve. 
- Finally, once we've figure out what recursive problem we really need to solve, we solve that problem by recursive brute force. Try everything, you can make the algorithm faster later. 
## Text Segmentation
- Suppose you are given a string of letters representing text in some foreign language, but without any spaces or punctuation, and you want to break this string into its individual constituent words. 
- We start by considering an extremely simple segmentation problem: given a string of characters, can it be segmented into English words at all?
- We assume that we have access to a subroutine isWord(w) that takes a string w as input and returns True if w is a word. 
- Just like the subsetsum problem, the input structure is a sequence, so it is natural to consider a decision process that consumes the input characters in order from left to right. 
- At any point in the process, we have to decide where the next word in the output sequence ends. 
- First, we find the first sequence of characters that makes a word. Then we let recursion work on the rest of the characters. 
- We iteratively find the next sequence to add to our previous set of characters that makes a word, and let recursion take care of the rest of the characters. We do this until we run out of characters, or recursion returns true. 
- Algorithm:
```
splilttable(A[1..n]):
	if n = 0:
		return True
	for i to n:
		if A[:i] is word:
			if splittable(A[i+1:]):
				return True
	return False
```
### Index Formulation
- In practice, passing arrays as input parameters is rather slow; we should really find a more compact way to describe our recursive subproblems. 
- For purpose of designing the algorithm, its incredibly useful to treat the original input array as a global variable and then reformulate the problem and the algorithm in terms of array indices. 
- For our string segmentation problem, the argument of any recursive call is always a suffix $A[i...n]$, of the original input array. So we can reformulate our recursive algorithm as: Given an index $i$, find a segmentation of the suffix $A[i\dots n]$. 
- Our recursive formulation becomes: $splittable(i)=\begin{cases}True & \text{if } i>n \\ \bigvee^{n}_{j=i}(iswor d(i, j) \Lambda splittable(j+1))&\text{otherwise} \end{cases}$
## Longest Increasing Subsequence
- For any sequence $S$, a subsequence of $S$ is another sequence obtained from $S$ by deleting zero or more elements without changing the order of the remaining elements. 
- An empty sequence is a subsequence of $S$ and $S$ is a subsequence of itself. 
- A subsequence whose elements are contiguous in the original sequence is called a substring. 
- Suppose we are given a sequence of integers, and we need to find the longest subsequence whose elements are in increasing order. 
- One natural approach to building this longest increasing subsequence is to decide for each index $j$ whether or not to include $A[j]$ in the subsequence. 
- If we imagine ourselves in the middle of the algorithm at a decision point, we can think of a black bar separating the part of the array we have already made decisions for and the number to the right of our black bar being the number we need to decide whether to include or not. 
- At a point, we may be able to include the number next to the black bar, but its not obvious whether we should, so we brute force it: 
	- Tentatively include the number and let recursion make the rest of the decisions. 
	- Tentatively exclude the number and let recursion make the rest of the decisions. 
- We always need to keep this key question: What do we need to remember about our past decisions?
	- We can only include $A[j]$ if the resulting subsequence is in increasing order. 
	- If we assume (inductively) that the numbers previously selected from $A[1..j-1]$ are in increasing order, then we can include $A[j]$ if it is greater than the last number selected from $A[1..j-1]$. Thus, the only information we need about the past is the last number selected so far. 
- Our recursive problem becomes: Given an integer $p r e v$ and an array $A[1..n]$, find the longest increasing subsequence of $A$ in which every element is larger than $p r e v$. 
- Our current strategy breaks down when we get to the end of the array because there is no next number to consider. But an empty array has exactly one subsequence, namely, the empty sequence. Thus the longest increasing subsequence of the empty array has length 0.
- Our algorithm:
```
LIS(prev, A[1..n]):
	if n == 0:
		return 0
	if A[1] <= prev:
		return LIS(prev, A[2..n])
	else:
		skip = 	LIS(prev, A[2..n])
		keep = LIS(A[1], A[2...n])+1
		return max(skip, keep)	
```
- We can reformulate this to use indices assuming our array is a global variable: given two indices $i$ and $j$ where $i<j$, find the longest increasing subsequence of $A[j\dots n]$ in which every element is larger than $A[i]$. 
- Let LIS(i, j) denote the length of the longest increasing subsequence of $A[j\dots n]$ in which every element is larger than $A[i]$. Our recursive strategy becomes: $LIS(i,j)=\begin{cases}0&\text{if }j>n\\ LIS(i, j+1)&\text{if }A[j]>A[i] \\ max\begin{cases}LIS(i, j+1)\\1+LIS(j,j+1)\end{cases}&otherwise\end{cases}$
- This is not the only backtracking strategy we can use to find the longest increasing subsequences. Instead of asking is $A[i]$ the next element of the output sequence, we could ask directly where is the next element of the output sequence. 
	- If we use this technique, we can only include numbers on the right that are greater than than the number in our longest increasing subsequence so far. 
	- To do so, we enumerate all possibilities by bruteforce. 
	- The subset of numbers we can consider as the next element depends only on the last number we decided to include.
	- We can reformulate our recursive problem as: Given an index $i$, find the longest increasing subsequence of $A[i\dots]$ that begins  with $A[i]$. 
	- Let LISFirst(i) denote the length of the longest increasing subsequence of $A[i\dots n]$ that begins with $A[i]$, and we reformulate our recursive definition as $LISfirst(i)= 1+max\{LISfirst(j)|j>i \cap A[j]>A[i]\}$. 
	```
	LISFirst(i):
		best = 0
		for j=i to n:
			if A[j] > A[i]:
				best = max(best, LISFirst(j))
			return best +1
	```
	- Finally, we need to reconnect this recursive algorithm to our original problem, finding the longest increasing subsequence without knowing its first element. 
	```
	LIS(A):
		best = 0
		for i to n:
			best = max(best, LIS(i))
		return best
	```

## Optimal Binary Search Trees
- Recall the running time for a successful search in a binary search tree is proportional to the number of ancestors of the target node. As a result, the worst-case search time is proportional to the depth of the tree. 
- In many applications of binary search trees, it is more important to minimize the total cost of several searches rather than the worst-case search time. If $x$ is a more frequent search target than $y$, we can save time by building a tree where the depth of $x$ is smaller than the depth of $y$. 
- Suppose we are given a sorted array of keys $A[1..n]$ and and array of corresponding access frequencies, $f[1..n]$. Our task is to build the binary search tree that minimizes the total search time, assuming that there will be exactly $f[i]$ searches for key $A[i]$. 
- We should first think of a good recursive definition of the function we are trying to optimize. If we are given a binary tree and a list of frequencies, the total cost becomes $\sum_{i=1}^{n}f[i] *a n c es t ors(v_{i})$. 
- Suppose $v_{r}$ is the root of $T$; be definition, $v_{r}$ is an ancestor of every node in $T$. If $i<r$, then all ancestors of $v_{i}$ except the root, are in the left subtree of $T$. Similarly the right if $i >r$. Thus we can partition our cost function thus $co st(T, f) = \sum^{n}_{i=1}f[i]+\sum_{i=1}^{r-1}f[i]a nc es tors_{left}(v_{i})+\sum_{i=r+1}^{n}f[i]anc estors_{right}(v_{i})$. 
- With simple substitution we get $co st(T, f)= \sum^{n}_{i=1}f[i]+Cost(left(t), f[1..r-1])+co st(right(t), f[r+1\dots n])$
- The base case for this recurrence is as usual $n=0$. The cost of performing no searches on an empty tree is zero. 