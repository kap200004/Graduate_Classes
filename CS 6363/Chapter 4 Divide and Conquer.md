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
- A recurrence T(n) is algorithmic if, for every sufficiently large threshold constant n_0 > 0, the following two properties hold:
	- For all $n < n_0$, we have $T(n) = \Theta(1)$.
	- For all $n \ge n_0$, every path of recursion terminates in a defined base case within a finite number of recursive invocations.