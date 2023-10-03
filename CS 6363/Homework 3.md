# Homework 3
## Longest Convex Subsequence
Call a sequence $x_{1}, \dots, x_{n}$ of numbers convex if $x_{i} < \frac{x_{i-1}+x_{i+1}}{2}$ for all $1<i<n$. Use dynamic programming to give an $O(n^3)$ time algorithm to compute the length of the longest convex subsequence of an arbitrary array $A[1\dots n]$ of $n$ integers. 

**Specification:** I want to find the largest number of elements in increasing order of the original array such that the previous and next element are greater than the current element when added together and divided by two. 

**Recursive Formulation:** At each step I need to make a decision whether to include the element $x_{i}$ or not. Whether we include $x_{i}$ or not is dependent on the last element in the previous longest subsequence but also the next term in the subsequence after $x_{i}$. I will keep an index $j$ of the last term in the previous longest convex subsequence and $k$ of the next term in the subsequence. If we have that $x_{i}< \frac{x_{j}+x_{k}}{2}$, then we want to return the max of 1 + the longest convex subsequence of $[x_{k}\dots n]$ with $x_{i}$ as the previous term and $x_{k+1}$ as the $k$ term, or the longest convex subsequence of $[x_{k}\dots n]$ with $x_{j}$ as the previous term and $x_{k+1}$ as the $k$ term. If we have that $x_{i}> \frac{x_{j}+x_{i+1}}{2}$ , then we want the longest convex subsequence of $[x_{i}\dots n]$ with $x_{k+1}$ as the $k$ term and $x_{j}$ as the previous term. Our initial call will have that $i=1, j=0, k=2$

**Trivial Cases**: If we have that $k$ is larger than the array, we have sweeped through the array, and return 0. 

**Recursive Non Dynamic Programming**
```
LCS(A, i, j, k):
	if k >= len(A):
		return 0
	if A[i] >= (A[j]+A[k])/2:
		return LCS(A, i, j, k+1)
	else:
		return max(1+LCS(A, k, i, k+1), LCS(A, k, j, k+1))
```

**Make it Dynamic**
- We have three indices which implies that we will need a three dimensional array, which we will call $D$. At any moment of our algorithm $D[i][j][k]$ is dependent on $D[i][j][k+1], D[k][i][k+1], D[k][j][k+1]$. We also know that $k$ comes after $i$ and $j$ comes before $i$. So we want to fill from our array going down from $k=n$ to $i$, and up from $j =1$ to $i$. So we can fill out our 3d array with a three for loops. Starting with $k=n$. We fill all $D[i][j][n+1]$ with zeros. 
```
LongestCOnvexDP(A):
	D = 3d array with D[i][n-1][n], and D[i][i][n] for all i being zeros 
	For k=n down to i:
		for i =k-1 down to zero:
			for j = i-1 down to zero:
				if A[i] >= (A[j]+A[k])/2:
					D[i][j][k] = D[i][j][k+1]
				else:
					D[i][j][k] = max(1+D[k][i][k+1], D[k][j][k+1])
```
## Paragraph Formatting
Consider the problem of neatly printing a paragraph on a page, using a font where all characters have the same width. The input is an array $L[1..n]$, where $L[i]$ is the number of characters of the $ith$ word to be printed. We want to print this paragraph neatly on some number of lines, where each line holds a maximum of $M$ characters. Our criterion of neatness is as follows. If a given line contains words $i$ through $j$, where $i\leq j$, and we leave exactly one space between words on the same line, then the number of extra spaces at the end of the line is $M-(j-i)-\sum_{k=i}^{j}L[k]$, which must be nonnegative so that the words fit on the line (You can assume that $L[i] \leq M$ for all $i$). We wish to minimize the sum over all lines except the last line, of the cubes of the numbers of extra space characters at the ends of the lines. Give an efficient algorithm. 


**Specification:** 
Optimal substructure: Let $space(i, j) = (M-(j-i)-\sum^{j}_{i}L[k])^3$. Let $Least(j, k)$ be the optimal line that ends with the $j$th word on line $k$. For all $i=1..j$ the optimal spacing on line $k$ would be $min_{i}(space(i,j)+Least(i-1, k-1))$. We do not know the optimal $k$ value but we know it can be at most $n$. So we would like to minimize over all $k=1\dots n$ our recursive definition becomes $min_{k}(min_{i}(space(i, j)+least(i-1, k-1)))$ Our initial call to Least will be with the arguments $j=n$ and $k=n$ and we will work our way down from $n$. 

**Trivial Cases**: 
If we have that $j<i$ then we have no words and our space is $M^3$. If we have that $k=n$ our space is $\sum_{i=1}^{n}(M-L[i])^3$ If $k=1$ our space is $(M-\sum_{i=1}^{n}L[k])^3$. To handle cases that are not possible, as in that space(i, j) > M, we will return infinity. 

**Recursive Non-dynamic**
```
L,M global variables, M being max words and L being our list of word lengths.

Least(j, k):
	
```