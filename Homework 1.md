### Problem 1. Running Time Analysis (18 points)

Provide tight asymptotic bounds (i.e. Θ(·)) on the worst case running times of the following two procedures. Please provide a very brief explanation of your answer. (7 points each)

(a)
```
procedure BackForwardAlg(n)
	if n≤10 then
		return n
	if neven then
		return BackForwardAlg(n/2)
	else
		return BackForwardAlg(n+ 3)
```

(b)
```
procedure RecursiveAlg(A[1 . . . n])
	if n== 1 then
		return False
	mid =⌈n/2⌉
	
	for i= 1 to mid do
		for j=mid + 1 to ndo
			if A[i] == A[j]then
				return True
				
	return (RecursiveAlg(A[1 . . . mid]) || RecursiveAlg(A[mid + 1 . . . n]))
```

(c) (4 points) Give a one sentence description of what RecursiveAlg does.

### Problem 2. Asymptotic Bounds (20 points)

Provide tight asymptotic bounds (i.e. Θ(·)) on the following. Correct answers are given full
points without explanation. (5 points each)

(a) $2/n +√n+ log^3n$
(b) The number of bits needed to write 10nin binary.
(c) Planet X has a current population of 1 billion. Assuming that the population of planet
X doubles every year, give an asymptotic bound on the population of planet X in 100
years from now.
(d) $\sum_{i=1}^{n}\log \frac{n}{i}$ [Hint: Stirling’s approximation may be useful (see Wikipedia).]

### Problem 3. Ordering functions (25 points)
Sort the following 25 functions from asymptotically smallest to asymptotically largest, indicating ties if there are any. You do not need to turn in proofs (in fact, please don’t turn in proofs).

42 lg nn n2.1lg∗(n) 1 + lg lg lg n

cos(n) + 2 √lg nlg n(lg∗n)lg nn5

lg∗222n

2lg n√nePn

i=1 iPn

i=1 i2

n7

(2n)n3/(2 lg n)12 + ⌊lg lg n⌋(lg n)lg n1 + 1

154 n

n1/lg lg nnlg lg nlg201 n n1/125 nlg4n

To simplify notation put all the functions in a single column, where $f(n)$ being above $g(n)$
in the column means $f(n) = o(g(n))$. If $f(n) = Θ(g(n))$, then write $f(n)$ and $g(n)$ separated
by a comma on the same line. For example, the functions $n^{2}, n, \begin{pmatrix} n \\2\end{pmatrix}, n^3$ should be written
•$n$
•$n^{2}$, $\begin{pmatrix} n \\ 2\end{pmatrix}$
•$n^3$

Hint: When considering two functions $f(n)$ and $g(n)$ it is sometimes useful to consider
the functions $\log f(n)$ and $\log g(n)$, since log f(n) = o(log g(n)) implies f(n) = o(g(n))
(but be careful, the implication does not work in the other direction, and in particular
log f(n) = O(log g(n)) does NOT imply f(n) = O(g(n))).

### Problem 4. Spacing (10 points)

To get into your local grocery store you must wait in line. Outside the front door there are
$n$ spaces in a single long row. Each space is either empty or has a single person. Due to
social distancing guidelines, people cannot stand in adjacent spaces (i.e. there must be at
least one empty space between them). Let $S(n)$ denote the total number of states this line
could be in (based on which spaces are occupied or not). For example, $S(3) = 5$ since the
possibilities are $\{eee, pee, epe, eep, pep\}$, where ’e’ denotes that the space is empty and ’p’
denotes that it has a person.

Write a recurrence for $S(n)$. Explain why this recurrence is correct. You do not need to
solve your recurrence. You should assume $S(0) = 1$. Hint: The recurrence should have a
simple form. Don’t forget to include base cases.

### Problem 5. Bounding Recurrences (27 points)
Provide tight asymptotic bounds for the following six recurrences (i.e. Θ(·)). If you cannot give matching upper and lower bounds, give the best upper and lower bounds you can. For the first three you must specify what the level sum (i.e. total cost) is of ith level in the recursion tree. For the last three you do not need to specify the level sum, but you should give a very brief explanation.

(a)$T(n) = 2T(n/2) + n^4$

(b) $T(n) = 16T(n/4) + n^2$

(c) $T(n) = 3T(n/2) + 5n$

(d) $T(n) = 2T(n/3) + T(n/4) + n$

(e) $T(n) = T(n−1) + √n$

(f) $T(n) = T(√n) + 7$