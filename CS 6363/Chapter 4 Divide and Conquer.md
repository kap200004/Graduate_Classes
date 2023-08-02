- For divide-and-conquer, you solve a given problem (instance) recursively.
- If the problem is small enough-the base case- you just solve it directly without recursing.
- Otherwise-the recursive case- you perform three characteristic steps:
	- Dive the problem into one or more subproblems that are smaller instances of the same problem.
	- Conquer the subproblems by solving recursively.
	- Combine the subproblem solutions to form a solution to the original problem.
### Recurrences
- A recurrence is an equation that describes a function in terms of its value on other, typically smaller, arguments.
- The general form of a recurrence is an equation or inequality that describes a function over the integers or reals using the function itself. It contains two or more cases, depending on the argument.
- If a case involves the recursive invocation of the function on different inputs, it is a recursive case.
- If a case does not involve a recursive invocation, it is a base case.
- The recurrence is well defined if there is at least one function that satisfies it, and ill defined otherwise.
### Algorithmic Recurrences
- A recurrence T(n) is algorithmic if, for every sufficiently large threshold constant $n_0 > 0$, the following two properties hold:
	- For all $n < n_0$, we have $T(n) = \Theta(1)$.
	- For all $n \ge n_0$, every path of recursion terminates in a defined base case within a finite number of recursive invocations.
### Conventions for Recurrences
* Whenever a recurrence is stated without an explicit base case, we assume that the recurrence is algorithmic. 
	* This means that we are free to pick any sufficiently large threshold constant $n_{0}$ for the range of base cases where $T(n) = \Theta(1)$. 
* Asymptotic solutions of algorithmic divide-and-conquer recurrences also don't tend to change when we drop any floors or ceilings in a recurrence defined on the integers to convert it to a recurrence defined on the reals. 
* You may sometimes see recurrences that are not equations, but rather inequalities, such as $T(n) \le 2T\left( \frac{n}{2} \right)+\Theta(n)$ because such a recurrence states only an upper bound on $T(n)$. we express its solutions using $O$-notation rather than $\Theta$-notation. 

### Divide-and-conquer and Recurrences
* Although it is common when using divide-and-conquer for all the subproblems to have the same size, that isn't always the case.  
* Although divide-and-conquer algorithms usually create subproblems with sizes a constant fraction of the original problem size, that's not always the case. 
	* For example, a recursive version of linear search creates just one subproblem, with one element less than the original problem. 

### Solving Recurrences
* There are three main methods for solving recurrences:
	* In the substitution method, you guess the form of a bound and then use mathematical induction to prove your guess correct and solve for constants. 
	* The recursion-tree method models the recurrence as a tree whose nodes represent the costs incurred at various levels of recursion. To solve the recurrence, you determine the costs at each level and add them up. 
		* Even if you don't use this method to formally prove a bound, it can be helpful in guessing the form of the bound for use in the substitution method. 
	* The master method- provides bounds for recurrences of the form $T(n) = aT( \frac{n}{b}) +f(n)$ where $a > 0$ and $b > 1$ are constants and $f(n)$ is a given "driving" function. 
		* It characterizes a divide-and-conquer algorithm that creates $a$ subproblems, each of which is $\frac{1}{b}$ times the size of the original problem, using $f(n)$ time for the divide and combine steps. 

### The Substitution Method for Solving Recurrences
* The substitution method comprises two steps: 
	* Guess the form of the solution using symbolic constants. 
	* Use mathematical induction to show that the solution works, and find the constants. 
* As an example of the substitution method, lets determine an asymptotic upper bound on the recurrence: $T(n) = 2T\left( \frac{n}{2} \right) + \Theta(n)$. 
	* We will guess the asymptotic time to be $O(n\log n)$ and use the substitution method to prove it. 
		* We adopt the inductive hypothesis that $T(n) \le cn\log n$ for all $n \ge n_{0}$, where we'll choose the specific constants $c > 0$  and $n_0 > 0$ later, after we see what constraints they need to obey. 
	* Assume by induction that this bound holds for all numbers at least as big as $n_{0}$ and less than $n$. In particular, therefore, if $n \ge 2n_{0}$, it holds for $\frac{n}{2}$, yielding $T\left( \frac{n}{2} \right)\leq c\frac{n}{2}\log\left( \frac{n}{2} \right)$ , substituting yields: 
		* $T(n) \le 2c \frac{n}{2} \log \frac{n}{2} + \Theta(n)$ 
		* $= cn \log n - cn \log 2 + \Theta(n)$
		* $= cn \log n -cn +\Theta(n)$
		* $\le cn\log n$
			* This last step holds if we constrain the constants $n_{0}$ and $c$ to be sufficiently larger that for $n \ge 2n_{0}$, the quantity $cn$ dominates the anonymous function hidden by the $\Theta(n)$ term. 
			* Most substitution proofs are done the same way. You ground the induction on a range of values from a convenient positive constant $n_{0}$ up to some constant $n'_{0}$ such that for $n \ge n'_{0}$ the recurrence always bottoms out in a constant-sized base case between $n_{0}$ and $n'_{0}$ , in this case $n'_{0} = 2n_{0}$. 

### The Master Method
* We call $f(n)$ a driving function, and we call a recurrence of the general form $T(n) = aT\left( \frac{n}{b} \right) + f(n)$ where $a > 0$ and $b >1$ a master recurrence. 
* To use the master method, you need to memorize three cases. 
* An algorithm that is defined by a master recurrence solves $a$ subproblems recursively, each in $T\left( \frac{n}{b} \right)$ time. 
* The driving function $f(n)$ encompasses the cost of dividing the problem before the recursion, as well as the cost for combining the results of the recursive solutions to subproblems. 
* The master method allows you to state a master recurrence without floors and ceilings and implicitly infer them because no matter how the arguments are rounded up or down to the nearest integer, the asymptotic bounds that it provides remain the same. 
### The Master Theorem
* let $a >0$ and $b>1$ be constants, and let $f(n)$ be a driving function that is defined and nonnegative on all sufficiently large reals. Define the recurrence $T(n)$ on $n \in \mathbb{N}$ by $T(n)= aT\left( \frac{n}{b} \right) + f(n)$, where $aT\left( \frac{n}{b} \right)$ actually means $a'T\left( \lfloor{\frac{n}{b}}\rfloor \right) + a''T\left( \lceil\frac{n}{b}\rceil \right)$ for some constants $a' \ge_{0}$ and $a'' \ge_{0}$ satisfying $a = a' +a''$. Then the asymptotic behavior of $T(n)$ can be characterized as follows: 
	* If there exists a constant $\epsilon >0$ such that $f(n) = O(n^{\log_{b}a-\epsilon})$, then $T(n) = \Theta(n^{\log_{b}a})$ . 
	* If there exists a constant $k \ge 0$ such that $f(n) = \Theta(n^{\log_{b}a}\log^kn)$, then $T(n) =\Theta(n^{\log_{b}a}\log^{k+1}n)$
	* 