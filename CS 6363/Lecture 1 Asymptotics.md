## What is an Algorithm
* An algorithm is an unambiguous, mechanically executable sequence of elementary instructions. 
* There are many types of algorithms: 
	* Deterministic vs. Randomized
	* Exact vs. Approximate
	* Offline vs. Online
	* Sequential vs. Parallel
* Algorithms are often viewed as an input $\succ$ output relation. 
* In algorithm analysis you index starting at 1 rather than 0, as is convention. 
* Typically any algorithm that checks all pairs of items will run in quadratic time. 
* When developing a randomized algorithm, we would like to talk about the average time complexity, but to do so would mean that we have to assume the distribution of our input. Rather, we should add the randomization to the input. I.e. shuffle the input, and enforce a random distribution.  
* It is important to never make an assumption about an algorithms runtime based on how many nested for loops it contains. A nested for loop does not always mean the algorithm is $O(n^2)$. 
# Function Growth
|         | 10| 100 | $10^3$ | $10^6$ | $10^9$ |
|---------|---|---|--|----|----|
|log n (binary search)| 1|2|3|6|9|
|$n$| 10|100|$10^3$|$10^6$|$10^9$|
|$n^2$ (pairs)| 100|$10^4$|$10^6$|$10^{12}$|$10^{18}$|
|$n^{10}$| $10^{10}$|$10^{20}$|$10^{30}$|$10^{60}$|$10^{90}$|
|$1.0001^n$|$1.01$|$1.1$|$3$|$10^{434}$|$10^{10^5}$|
|$2^n$ (Size of a Power Set)|$10^{3}$|$10^{30}$|$10^{301}$|$10^{10^5}$|$10^{10^8}$|
|$n!$|$10^{6}$|$10^{158}$|$10^{2567}$|$10^{10^6}$|$10^{10^{10}}$|

* Exponentials *always* dominate polynomial functions.
- Let $f(n), g(n)$ be function from $\mathbb{N}$ to $\mathbb{N}$, $f(n) = O(g(n))$ if and only if there exists an $n_{0} \in \mathbb{N}$ and $c \in \mathbb{R^+}$ such that for all $n > n_{0}, ~ f(n) \leq cg(n)$. 
- $\lim_{ n \to \infty } \frac{f(n)}{g(n)} \neq \infty$. 
### Limits of Asymptotic Notation
| $f(n)=$ |$\lim_{ n \to \infty } \frac{f(n)}{g(n)}$|Intuitive Meaning|In Other Terms|
|-----|-----|-----|------|
|$O(g(n))$|$\neq \infty$|$\leq$|None|
|$\Omega(g(n))$|$\neq 0$|$\geq$|None|
|$\Theta(g(n))$|$= k$|=|$\Omega \cap O$|
|$o(g(n))$|$=0$|<|$O \cap \bar{\Omega}$|
|$\omega(g(n))$|$= \infty$|>|$\Omega \cap \bar{O}$|

* In terms of asymptotic growth, Exponential always beats polynomial, and polynomial always beats polylogarithmic. 
 

















