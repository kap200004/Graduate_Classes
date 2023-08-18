Create flashcards in this format according to the guidelines and examples based on the info below.

Format:
create anki flashcards in this format:
First the front of the card is written in plain text, Put a ; at the end. Then the answer is put after a space in quotes ” “. For example, Question; “Answer”.
There should be no other formatting, each new line should be a flash card. 
save these flash cards to a .txt file for importing into anki.
For questions and answers that require mathematical symbols, the mathematical symbols should be typed in mathJax rather than latex. 

Guidelines:

Make flashcards only on the most important information, but make sure it comprehensively covers all of the material. There should be about 35-50 flash cards in total. 
Make sure the questions are clear and easy to understand
Make the answers very concise and about a single concept or fact

Examples:

Where is the Dead Sea located?; “on the border between Israel and Jordan”
What is the lowest point on the Earth’s surface?; “The Dead Sea shoreline”
What is the average level on which the Dead Sea is located?; “400 meters (below sea level)”
How long is the Dead Sea?; “70 km”

Info:
### Introduction
- When we look at input sizes large enough to make relevant only the order of growth of the running time of an algorithm, we are studying the asymptotic efficiency of algorithms. 
	- We are concerned with how the running time of the algorithm increases with the size of the input in the limit, as the size of the input increases without bound. 
- Usually, an algorithm that is asymptotically more efficient is the best choice for all but very small inputs. 
### $O$-notation
- $O$-notation characterizes an upper bound on the asymptotic behavior of a function. It states that a function grows no faster than a certain rate, based on the highest-order term. 
- We can write a function whose highest term is $n^3$ as being $O(n^3)$, but we can also write such a function as being $O(n^4)$ because the function grows more slowly than $n^4$. 
	- More generally, it is $O(n^c)$ for any constant $c \ge 3$. 
- The formal definition:
	- $O(g(n)) = \{f(n): \text{there exist positive constnants c and } n_{0} \text{ such that } 0 \le f(n) \le cg(n) \text{ for all n } \geq n_{0}\}$ 
	- The definition of $O(g(n))$ requires that every function $f(n)$ in the set $O(g(n))$ be asymptotically nonnegative: $f(n)$ must be nonnegative whenever $n$ is sufficiently large.
		- Consequently, the function $g(n)$ must be asymptotically nonnegative, or else the set $O(g(n))$ is empty. 
### $\Omega$-notation
- $\Omega$-notation characterizes a lower bound on the asymptotic behavior of a function. It says that a function grows at least as fast as a certain rate based on the highest order term.
- A function whose highest order term is $n^3$ is $\Omega(n^3)$, and is also $\Omega(n^2)$, and so on.
	- More generally, it is $\Omega(n^c)$ for any constant $c \le 3$
- Formal Definition: 
	- $\Omega(g(n)) = \{f(n): \text{there exist postive and constants c and } n_{0} \text{ such that } 0 \leq cg(n) \leq f(n) \text{ for all } n \geq n_{0}\}$
### $\Theta$-notation
- $\Theta$-notation characterizes a tight bound on the asymptotic behavior of a function. it says that a function grows precisely at a certain rate, based on the highest order term. 
- Formally, $\Theta$-notation characterizes the rate of growth of the function to within a constant factor from above and to within a constant factor from below. 
- If you can show that a function is both $O(f(n))$ and $\Omega(f(n))$ for some function $f(n)$, then you have shown that the function is $\Theta(f(n))$. 
- Formal Definition:
	- $\Theta(g(n)) = \{f(n): \text{there exist postive and constants c1, c2 and } n_{0} \text{ such that } 0 \leq c_{1}g(n) \leq f(n) \leq c_{2}g(n) \text{ for all } n \geq n_{0}\}$
- For any two functions $f(n)$ and $g(n)$, we have $f(n) = \Theta(g(n))$ if and only if $f(n) = O(g(n))$ and $f(n) = \Omega(g(n)$. 
### Asymptotic Notation in Equations and Inequalities
- When the asymptotic notation stands alone on the right-hand side of an equation or inequality, the equal sign means set membership.
- When asymptotic notation appears in a formula, we interpret it as standing for some anonymous function that we do not care to name. 
- Using asymptotic notation in this manner can help eliminate inessential detail and clutter in an equation. 
### $o$-notation
- They asymptotic upper bound provided by $O$-notation may or may not be asymptotically tight. 
- The bound $2n^{2}= O(n^2)$ is asymptotically tight, but the bound $2n = O(n^2)$ is not. 
- We use $o$-notation to denote an upper bound that is not asymptotically tight. 
- Formal Definition:
	- $o(g(n)) = \{f(n):\text{for any positive constant } c > 0 \text{, there exists a constant } n_{0} > 0\text{ such that } 0 \leq f(n) < cg(n) \text{ for all } n \geq n_{0}\}$. 
- The definitions of $O(n) \text{ and } o(n)$ are similar, except that for that $f(n) = O(g(n))$ the bound $0 \leq f(n) < cg(n)$ holds for -some- constant, while for $o(g(n))$ it holds for any constant. 
- Intuitively, in $o$-notation, the function $f(n)$ becomes insignificant relative to $g(n)$ as n gets large: $\\lim_{ n \to \infty } \frac{f(n)}{g(n)}=0$. 
### $\omega$-notation
- By analogy, $\omega$-notation is to $\Omega$-notation as $o$-notation is to $O$-notation. 
- One way to define it is by $f(n) \in \omega (n) \text{ if and only if }g(n)\in o(f(n))$. 
- Formal definition: 
	- $\omega(g(n)) = \{f(n):\text{for any positive constant } c > 0 \text{, there exists a constant } n_{0} > 0\text{ such that } 0 \leq cg(n) < f(n) \text{ for all } n \geq n_{0}\}$
### Standard Notations and Common Functions
- A function $f(n)$ is monotonically increasing if $m \leq n$  implies $f(m) \leq f(n)$. 
- A function $f(n)$ is monotonically decreasing if $m \leq n$ implies $f(m) \geq f(n)$.
- A function $f(n)$ is strictly increasing if $m \leq n$  implies $f(m) < f(n)$. 
- A function $f(n)$ is strictly decreasing if $m \leq n$ implies $f(m) > f(n)$.
- An important rule to remember about floors and ceilings is that $- \lfloor x \rfloor =  \lceil-x \rceil$ and equivalently $- \lceil x \rceil = \lfloor -x \rfloor$. 
- For any integer n and real number x, we have $\lfloor n +x \rfloor = n + \lfloor x \rfloor$ and $\lceil n +x \rceil = n + \lceil x \rceil$. 
- For any integer a and any positive integer n, the value a mod n is the remainder of the quotient a/n: $a \text{ mod } n = a -n \lfloor \frac{a}{n} \rfloor$. 
- a is equivalent to b, modulo n if a and b both have the same remainder when divided by n. It can be said equivalently that $a = b ~(\text{ mod n})$ if and only if n is a divisor of $b-a$. 
- Given a nonnegative integer d, a polynomial in n of degree d is a function p(n) of the form: $p(n) = \sum_{i =0}^{d} a_{i}n^i$ where the constants $a_{1}\dots a_{i}$ are the coefficients of the polynomial and $a_{i} \neq 0$. 
- For an asymptotically positive polynomial ($a_{i} > 0$) $p(n)$ of degree d, we have $\Theta(n^d)$. 
- We say that a function $f(n)$ is polynomially bounded if $f(n) = O(n^k)$ for some constant $k$. 
- For all real $a >0$, m and n, we have the following identities:
	- $a^{0}= 1$. 
	- $a^{1}=a$
	- $a^{-1}= \frac{1}{a}$. 
	- $(a^{m})^{n} = a^{mn}$
	- $(a^{m})^{n} = (a^{n})^m$ 
	- $a^{m}a^{n}= a^{m+n}$
- When convenient, we assume that $0^{0}= 1$. 
- $e^{x}= 1 +x +\frac{x^{2}}{2!}+ \frac{x^{3}}{3!}+\dots = \sum_{i=0}^{\infty} \frac{x^{i}}{i!}$
- For all real x, we have the inequality $1+x \leq e^x$ where the equality holds only when $x=0$ .
- The following notation is always used with computer science writing: 
	- $\log n = \log_{2}n$ binary logarithm
	- $\ln n = \log_{e}n$ natural logarithm
	- $\log^{k}n =\log(n)^{k}$ exponentiation
	- $\log \log n = \log(\log(n))$ composition. 
- We adopt the following notational convention: in the absence of parentheses, a logarithm function applies only to the next term in the formula, so that $\log n +1 = (\log n)+1$. 
- For all real $a >0, b>0 \text{ and }c>0$ we have: 
	- $a = b^{\log_{b}a}$. 
	- $\log_{c }(ab)= \log_{c}a +\log_{c}b$. 
	- $\log_{b}a^{n}= n \log_{b}a$.
	- $\log_{b}a = \frac{\log_{c}a}{\log_{c}b}$. 
	- $\log_{b} \frac{1}{a} = -\log_{b}a$. 
	- $\log_{b}a = \frac{1}{\log_{a}b}$. 
	- $a^{\log_{b}c} = c^{\log_{b}a}$. 
- We say that a function $f(n)$ is polylogarithmically bounded if $f(n)=O(\log^{k}n)$ for some constant $k$. 
- Any positive polynomial function grows faster than any polylogarithmic function. 
- 0! = 1
- A weak upper bound on the factorial function is $n! \leq n^n$.
- We have that:
	- $n! = o(n^n)$
	- $n! = \omega(2^n)$. 
	- $\log(n!) = \Theta(n \log n)$. 
- We use the notation $f^{i}(n)$ to denote the function $f(n)$ iteratively applied $i$ times to an initial value of $n$. For example, if $f(n)=2n$ then $f^{i}(n) = 2^{i}n$. 

