### Properties of the Log function
* $C^{\log_{c}n}=n \text{ for } c>1$. 
* Base exchange formula: $\log_{b}n=\frac{\log_{a}n}{\log_{a}b} \text{ for } a,b>1$
* $a^{\log n}=n^{\log a}$ and we can derive this from the exponent rule of logs and taking the log of both sides.
* The log of a polynomial is $\Theta$(log(n)) for any polynomial. 
* log n is to n as n is to $2^n$. 
* $\log^{*2^{2^{n}}}= 1+\log^{*}2^{n}=2 +\log^*n$. This is known as the iterated logarithm. 
* $\log^*n=o(\log \log \log\dots \log n)$. 
### Useful Trick
* Want to determine if $f(n)=o(g(n))$, but the functions have complex exponential terms? Taking a log pulls down the exponential term. 
* This occurs because the logarithmic function is monotonically increasing. 
	* if $\log(f(n)) = o(\log(g(n))), then f(n) = o(g(n))$. 
* Here is an example: 
	* $f(n)=n^{\log n}, g(n)=\log^\sqrt{ n }n$
	* $\log(f(n))=\log^{2}n$
	* $\log(g(n))=\sqrt{ n }\log \log n$. 
	* $\log^2n=o(\sqrt{ n }\log \log n)$ why? because the $\sqrt{ n }$ is a polynomial, and $\log^2n$ remains polylogarithmic and polylogarithmic functions are always little oh of polynomial. 
* It is important to remember that this is only true for little oh, not big oh. 
### Common Series
* Harmonic: $\sum^{n}_{i=1} \frac{1}{i}=\Theta(\log n)$. 
* Geometric: $\sum^{n-1}_{i=0} x^i= \frac{x^{n}-1}{x-1}=\Theta(x^n)$, when x is greater than 1. If x is less than 1, it is $\Theta(1)$ x is some positive constant. 
* Arithmetic: $\sum^{n}_{i=1}i=\frac{(n+1)n}{2}=\Theta(n^2)$
### Induction
* We use induction to prove statements for all $n \in \mathbb{N} \text{ s.t. } n\geq n_{0}$.
* The steps:
	* Base Cases: Prove statement for some $n_{0}$, often for $n_{0}=0 \text{ or }1$. 
	* Inductive Hypothesis: Assume statement holds for all $m \geq n$. Prove it holds for $n+1$
### Recursion
* Recursion is the twin brother of induction. It is the same movie, just backwards. 
* Reduction- Solve problem A using a black box for problem B. Typically B is some sort of smaller or simpler problem. We don't want to open the black box for B!
* Recursion is a type of reduction. If the problem size is tiny, we need to just solve it. Other wise, we need to reduce the problem to one or more smaller instances of the same problem. 
* How are the smaller, but not tiny base case, subproblems solved? It's not your problem. You are not suppose to thing about this. It is a black box, and you don't think about how it is solved. 
### Tower of Hanoi
* The setup: 
	* There are 3 pegs holding n distinct sized disks. 
	* Initially, the two pegs named temporary and destination are empty, and the source peg has all n disks sorted. 
	* Our goal is to move all of the disks to the destination peg. 
	* Larger disks cannot be placed on smaller disks. 
	* Only one disk can move at a time. 
	* How many moves does it take? 
*  We start by thinking about the simple case, where we start with just one disk, or 0 disks, in which we do nothing. For the case of having one disk, we simply, move it to the destination peg. 
* For the case of two disks, we move the top the temporary peg, the bottom to the destination peg, and then then the top on from the temporary peg to the destination.  
* The cases quickly become intractable, so how do we design an algorithm for n disks? 
	* Our natural inclination would be that we must first consider the disk on top, and what to do with the disk. BUT!, this is the wrong thing to do. Instead, we consider the bottom disk first. 
	* What do I need to do to move the largest disk to destination? I know several things that are necessary for this: 
		* The destination peg has to be empty. 
		* The source has only the largest disk. 
		* The temporary peg must have n-1 disks in sorted order. 
	* I don't know how to get to the above configuration, but I know I have to have that configuration. 
	* So:
		* We must move n-1 smaller disks from the source to the temp. 
		* We have to move the largest disk from the source to the destination. 
		* We have to move the n-1 smaller disks from the temporary peg to the destination peg. 
		* This is the algorithm, we don't think about how to move the n-1 disks. A caveat is we need to know how to move 0 disks. 
		```python
		Hanoi(n, source, destination, temporary):
			if n > 0:
				Hanoi(n-1, source, temporary, destination)
				move disk n from source to destination
				Hanoi(n-1, temporary, destination, source)
```
#### Solving the Hanoi Run time
* It is clear to see that at every level of recursion, our algorithm does O(1) work. 
* We see that because we make two recursive calls, there must be two branches from each node. 
* We see that because each level is one less than the previous level, our recursion tree's height must be n. 
* We can now see that at the nth level we will have $2^{n-1}$ nodes. This is a binary tree of height n. 
* In all ***full*** binary trees, there are exact $2(2^{n-1})-1$ nodes or, $2^{n}-1$. 
