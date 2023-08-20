### Fundamental Probability Rules
* Given two events, A and B, we define the probability of A or B as follows: 
	* $P(A \cup B)= P(A) + P(B) - P(A \cap B)$ or, 
	* simply $P(A)+P(B)$ if A and B are mutually exclusive. 
* We define the probability of the joint event A and B as follows: 
	* $P(A, B) = P(A \cap B)=P(A |B)P(B)$ -this is known as the product rule. 
* Given a joint distribution on two events $p(A, B)$, we define the marginal distribution as follows: 
	* $P(A)= \sum_{b}p(A, B)= \sum_{b}P(A|B=b)P(B=b)$, where we are summing over all possible states of B.
	* This is called the sum rule or the rule of total probability. 
* The product rule can be applied multiple times to yield the chain rule of probability: 
	* $P(X_{1:D}) = P(X_{1})P(X_{2}|X_{1})P(X_{3}|X_{2}X_{1})P(X_{4}|X_{3}, X_{2}, X_{1})\dots P(X_{D}|X_{1:D-1})$. 
* We define the conditional probability of event A, given that event B is true, as: 
	* $P(A|B)=\frac{P(A, B)}{P(B)} \text{ if }P(B) > 0$. 
* Combining the definition of conditional probability with the product and sum rules yields Bayes' rule, also called Bayes' Theorem: 
	* $P(B|A) = \frac{P(B, A)}{ P(B)} = \frac{P(A|B)P(B)}{P(A)} = \frac{P(A|B)P(B)}{\sum_{x'}P(B=x')P(A | B=x')}$.
* We say X and Y are unconditionally independent or marginally independent, if we can represent the joint as the product of the two marginals, i.e. $P(X, Y) = P(X)P(Y)$. 
* We say that X and Y are conditionally independent given Z if and only if the conditional joint can be written as a product of conditional marginals, i.e. $P(A, B|Z) = P(A|Z)P(B|Z)$. 
	* Another characterization of conditional independence is this: X and Y are conditionally independent give Z if and only if there exists functions g and h such that: $P(x, y|z) = g(x,z)h(y,z)$. 
### Continuous Random Variables
* Suppose X is some uncertain continuous quantity. The probability that X lies in any interval $a \leq X \leq B$ can be computed as follows:
	* $P(a <X\leq b)= F(b)-F(a)$ where $F(a)= P(X \leq a)$ and $F(b) = P(X \leq b)$. 
	* This is called the cumulative distribution function of X. 
* Now define $f(x) = \frac{d}{dx}F(x)$, we call this the probability density function. 
* Given a pdf, we can compute the probability of a continuous variable being in a finite interval as follows: 
	* $P(a < X\leq b) = \int  ^{b}_{a} f(x) \, dx$. 
	* As the size of the interval gets smaller, we can write $P(x < X \leq x+ dx) = P(x)dx$. 
### Quantiles 
* 