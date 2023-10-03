- Sometimes, we can speed up our recursive algorithms considerably by writing down the results of our recursive calls and looking them up again if we need them later. This optimization technique is known as memoization. 
- Once we have seen how an array is filled using memoization, we can replace the memoized recurrence with a simple for-loop that intentionally fills the array in that order, instead of relying on a more complicated recursive algorithm to do it for us accidentally.
- In many dynamic programming algorithms, it is not necessary to retain all intermediate results through the entire computation. 
- In a nutshell, dynamic programming is recursion without repetition. Dynamic programming algorithms store the solutions of intermediate subproblems, often but not always in some kind of array or table. 
- Dynamic programming algorithms are best developed in two distinct stages: 
	- Formulate the problem recursively - write down a recursive formula or algorithm for the whole problem in terms of the answers to smaller subproblems. A complete recursive formulation has two parts: 
		- Specification- Describe the problem that you want to solve recursively in coherent and precise English- not how to solve that problem, but what problem you're trying to solve. 
		- Solution- give a clear recursive formula or algorithm for the whole problem in terms of the answers to smaller instances of *exactly* the same problem. 
	- Build solutions to your recurrence from the bottom up - write an algorithm that starts with the base cases of your recurrence and works its way up to the final solution, by considering intermediate subproblems in the correct order. This state can be broken down into several smaller mechanical steps: 
		- Identify the subproblems- What are all the different ways your recursive algorithm can call itself, starting with some initial input. 
		- Choose a memoization data structure- find a data structure that can store the solution to every subproblem you identified in the step above. This is usually, but not always, a multidimensional array. 
		- Identify dependencies- except for the base cases, every subproblem depends on other subproblems. Draw a picture of your data structure, pick a generic element, and draw arrows from each of the other elements it depends on. Then formalize your picture. 
		- Find a good evaluation order- order the subproblems so that each one comes after the subproblems it depends on. You should consider the base cases first, then the subproblems that depends only on base cases, and so on. 
		- Analyze space and running time- The number of distinct subproblems determines the space complexity. To compute the total running time, add up the running times of all possible subproblems, assuming deeper recursive calls are already memoized. 
		- Write down the algorithm- You know what order to consider the subproblems, and you know how to solve each subproblems. So do that! If your data structure is an array, this usually means writing a few nested for-loops around your original recurrence, and replacing the recursive calls with array lookups. 
## Longest Increasing Subsequence
- We defined $LISbig ger(i, j)= \begin{cases}0&\text{if j>n} \\ LisBig(i, j+1)&\text{if } A[i]\geq A[j]\\max \begin{cases}LisBig(i, j+1)\\1+LisBig(j, j+1)\end{cases}& \text{otherwise}\end{cases}$ when we were discussing backtracking and finding the longest increasing subsequence. 
- To solve the original problem, we can add a sentinel value $A[0]= -\infty$ to the array and compute $LIS(0,1)$. This is because the longest increasing subsequence of only one number is one. 
- Each recursive subproblem is identified by two indices $i$ and $j$, so there are only $O(n^2)$ distinct subproblems to consider. We can memoize the results of these subproblems into a two dimensional array.
- The order in which the memoized recursive algorithm fills this array is not immediately clear; all we can tell from the recurrence is that each entry $LIS[i, j]$ is filled after the entries $Lis[i, j+1]$ and $Lis[j, j+1]$. 
	- This partial information can be used to give us a valid evaluation order.
	- If we fill the table, one column at a time, from right to left, then when ever we reach an entry in the table, the entries it depends one already available. 
```
LisDP(A):
	A[0] = -infty
	for i to n:
		LIS[i, n+1]=0 # a two dimensional array
	for j =n down to 1:
		for i 0 to j-1:
			keep = 1+LIS[j, j+1]
			skip = LIS[i, j+1]
			if A[i] > A[j]:
				LIS[i, j] = skip
			else:
				LIS[i, j] = max(keep, skip)
	return LIS[0, 1]
		
```
## Edit Distance
- The edit distance between two strings is the minimum number of letter insertions, letter deletions, and letter substitutions required to transform one string into another. 
- We can visualize this editing process by aligning the strings one above the other, with a gap in the first word for each insertion and a gap in the second word for each deletion. 
- Columns with two different characters correspond to substitutions. 
- To develop a dynamic programming algorithm to compute edit distance, we first need to formulate the problem recursively. 
- Our alignment representation for edit sequences has a crucial "optimal substructure" property. Suppose we have the gap representation for the shortest edit sequence for two strings. If we remove the last column, the remaining columns must represent the shortest edit sequence for the remaining prefixes. 
- We can easily prove this observation by contradiction: if the prefixes had a shorter edit sequence, gluing the last column back on would give us a shorter edit sequence for the original strings. 
- So once we figure out what should happen in the last column, recursion can figure out the rest of the optimal gap representation. Said differently, the alignment we are looking for represents a sequence of editing operations ordered from right to left. 
- Solving the edit distance problem requires making a sequence of decisions, one for each column in the output alignment. 
- In the middle of this sequence of decisions, we have already aligned the suffix of one string with the suffix of the other. Our remaining decisions don't depend on the editing operations we have already choses but on the prefixes we have not yet aligned.
- Recursive Formulation: for any indices $i$ and $j$, let Edit($i, j$) denote the edit distance between prefixes $A[1..i]$ and $B[1\dots j]$.  When $i$ and $j$ are both positive, there are exactly three possibilities for the last column in the optimal alignment of $A[1\dots i]$ and $B[1\dots j]$.
	- Insertion - the last entry in the top row is empty. In this case, the edit distance is equal to Edit(i, j-1)+1. The +1 being the cost of the final insertion. 
	- Deletion- The last entry in the bottom row is empty. In this case the edit distance is equal to $Edit(i-1, j)+1$. 
	- Substitution- Both rows have characters in the last column. If these two characters are different then the edit distance is Edit(i-1, j-1) + 1, and if they are the same it is simply Edit(i-1, j-1). 
- This generic case analysis breaks down if either $i=0$ or $j=0$, but those boundary cases are easy to handle:
	- Edit(0, j) = j because transforming the empty string into a string of length j requires j insertions. 
	- Edit(i, 0) = i because transforming a string of length i to the empty string requires i deletions. 
- For our recursive definition we get $edit(i,j)=\begin{cases}i &\text{if } j==0\\ j & \text{if } i==0 \\ min \begin{cases}edit(i, j-1)+1 \\edit(i-1, j)+1 \\ edit(i-1, j-1)+A[i]\neq B[j]\end{cases}& \text{otherwise} \end{cases}$
- 