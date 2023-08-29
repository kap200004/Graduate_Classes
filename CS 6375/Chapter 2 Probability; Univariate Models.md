## Introduction
### What is Probability? 
* There are actually two different interpretations of probability: 
	* The frequentist interpretation views probabilities as long run frequencies of events that can happen multiple times. 
	* In the Bayesian interpretation, probability is used to quantify our uncertainty or ignorance about something: hence it is fundamentally related to information rather than repeated trials. 
### Types of Uncertainty
* Two fundamentally different reason can cause uncertainty in our predictions to arise: 
	* Epistemic uncertainty- is due to our ignorance of the underlying hidden causes or mechanism generating our data. A simpler term for this is model uncertainty. 
	* Aleatoric uncertainty, or data uncertainty, arises from intrinsic variability, which cannot be reduced even if we collect more data. 
### Probability as an Extension of Logic
* The basic rules of probability are viewed as an extension of Boolean logic. 
#### Probability of an Event
* We define an event, denoted by the binary variable $A$, as some state of the world that either holds or does not hold. 
* The expression $Pr(A)$ is the probability with which you believe event $A$ is true. 
* $Pr(\bar{A})=1-Pr(A)$
#### Probability of a Conjunction of Two Events
* We denote the joint probability of events A and B both happening as follows: 
	* $Pr(A \cap B)=Pr(A,B)$
* If $A$ and $B$ are independent events, we have
	* $Pr(A,B)=Pr(A)Pr(B)$ 
#### Probability of a Union of Two Events
* The probability of event $A$ or $B$ happening is given by
	* $Pr(A \cup B)=Pr(A)+Pr(B)-Pr(A \cap B)$
* If the events are mutually exclusive (so they cannot happen at the same time), we get
	* $Pr(A \cup B)=Pr(A)+Pr(B)$
#### Conditional Probability of One Event Given Another
* We define the conditional probability of event $B$ happening given that $A$ has occurred as follows: 
	* $Pr(B|A)=\frac{Pr(A,B)}{Pr(A)}$
* This is not defined if $Pr(A)=0$, since we cannot condition on an impossible event. 
#### Independence of Events
* We say that event $A$ is conditionally independent of event $B$ if 
	* $Pr(A, B)=Pr(A)Pr(B)$
#### Conditional Independent of Events
* We say that events $A$ and $B$ are conditionally independent given event $C$ if: 
	* $P(A, B|C)=Pr(A|C)Pr(B|C)$. 
	* This is also written $A \bot B|C$
* Events are often dependent on each other, but may be rendered independent if we condition on the relevant intermediate variables. 
## Random Variables
* Suppose $X$ represents some unknown quantity of interest. If the value of $X$ is unknown and/or could change, we call it a random variable. 
* The set of possible values of $X$ is known as the sample space or state space. 
* An event is a set of outcomes from a given sample space. 
### Discrete Random Variables
* If the sample space is finite or countably infinite, then $X$ is called a discrete random variable. 
* In this case, we denote the probability of the event that $X$ has a value $x$ by $Pr(X=x)$.
* We define the probability mass function or pmf as a function which computes the probability of events which correspond to setting $X$ to each possible value. 
* $p(x) \equiv Pr(X=x)$. 
* The pmf satisfies the properties $0\leq p(x)\leq 1$ and $\sum_{x \in X}p(x)=1$. 
### Continuous Random Variables
* If $x \in \mathbb{R}$ is a real-valued quantity, it is called a continuous random variable, and we an no longer create a finite (or countable) set of distinct possible values it can take on. 
* There are a countable number of ***intervals*** which we can partition the real line into. 
* By allowing the size of the intervals to shrink to zero, we can represent the probability of $X$ taking on a specific real value. 
#### Cumulative Distribution Function
* Define the events $A=(X\leq a), B=(X\leq b), \text{ and }C=(a<X\leq b)$, where $a<b$. We have that $B=A\cup C$ and since $A \text{ and }C$ are mutually exclusive, the sum rule gives us: $Pr(B)=Pr(A)+Pr(C)$. 
* And hence, the probability of being in interval $C$ is given by: $Pr(C)=Pr(B)-Pr(A)$. 
* In general, we define the cumulative distribution function or cdf of $X$ as $P(x)\equiv Pr(X\leq x)$. 
* Knowing the cdf, we can compute the probability of being in any interval as: $Pr(a<X\leq b)=P(b)-P(a)$. 
* Cdf's are monotonically non-decreasing functions. 
#### Probability Density Function
* We define the probability density function or pdf as the derivative of the cdf: $p(x) \equiv \frac{d}{dx}P(x)$. 
* Given a pdf, we can compute the probability of a continuous variable being in a finite interval as follows: $Pr(a<X\leq b)=\int _{a}^{b}p(x) \, dx=P(b)-P(a)$. 
* As the size of the interval gets smaller, we can write $Pr(x\leq X\leq x+dx)\approx p(x)dx$
* Intuitively, this says the probability of $X$ being in a small interval around $x$ is the density at $x$ times the width of the interval. 
#### Quantiles
* If the cdf P is strictly monotonically increasing, it has an inverse, called the inverse cdf, or percent point function or quartile function. 
* If P is the cdf of $X$, then $P^{-1}(q)$ is the value $x_{q}$ such that $Pr(X\leq x_{q})=q$ . 
* This is called the $qth$ quantile of $P$. 
* The value $P^{-1}(.5)$ is the median of the distribution, with half of the probability mass on the left, and half on the right. 
* The values $P^{-1}(.25) \text{ and }P^{-1}(.75)$ are the lower and upper quartiles. 
### Sets of Related Random Variables
* We can define the joint distribution of two random variables using $p(x, y)=p(X=x, Y=y)$ for all possible values of $X$ and $Y$. 
* If both variables have finite cardinality, we can represent the joint distribution as a two-dimensional table, all ow whose entries sum to one. 
* An example:

| $p(X, Y)$ | $Y=0$ | $Y=1$ |
| --- | --- | ---|
| $X = 0$ | $0.2$ | $0.3$ |
| $X = 1$ | $0.3$ | $0.2$ |

- If two variables are independent, we can represent the joint as the product of two marginals. 
- Given a joint distribution, we define the marginal distribution of $X$ as: $p(X=x)=\sum_{y}p(X=x, Y=y)$ where we are summing over all possible states of $Y$. 
- This is sometimes called the sum rule or the rule of total probability. 
- We define the conditional distribution of a random variable using: $p(Y=y|X=x)=\frac{p(X=x, Y=y)}{p(X=x)}$ which we can rearrange to get $p(x, y)=p(x)p(y|x)$ which is called the product rule. 
- By extending the product rule to $D$ variables, we get the chain rule of probability: $p(x_{1:d})=p(x_{1})p(x_{2}|x_{1})p(x_{3}|x_{1}, x_{2})p(x_{4}|x_{1}, x_{2}, x_{3})\dots p(x_{D}|x_{1:D-1})$
	- This provides a way to create a high dimensional joint distribution from a set of conditional distributions. 
### Independence and Conditional Independence
* We say $X \text{ and }Y$ are unconditionally independent or marginally independent, denoted $X \bot Y$, if we can represent the joint as the product of two marginals, i.e., $X \bot Y \iff p(X,Y)=p(X)p(Y)$. 
* In general, we say a set of variables $X_{1}, \dots, X_{n}$ is independent if the joint can be written as a product of marginals, ,i.e., $p(X_{1}, \dots, X_{n})=\Pi_{i=1}^{n}p(X_{i})$. 
* We say $X$ and $Y$ are conditionally independent given $Z$ iff the conditional joint can be written as a product of conditional marginals: $X \bot Y |Z \iff p(X, Y|Z)=P(X|Z)P(Y|Z)$. 
* We can write this assumption as a graph $X-Z-Y$, which captures the intuition that all the dependencies between $X$ and $Y$ are mediated via $Z$. 
### Moments of Distribution
* Various summary statistics that can be derived from a probability distribution. 
#### Mean of a Distribution
* We denote the mean, or expected value, as $\mu$. 
* For continuous random variables, the mean is defined as: $\int _{\mathbf{X}}xp(x) \, dx$. 
* If the integral is not finite. the mean is not defined. 
* For discrete random variables the mean is defined as follows: $\sum_{x\in\mathbf{X}}xp(x)$. However this is only meaningful if the values of $x$ are ordered in some way (e.g., if they represent integer counts). 
#### Variance of a Distribution
- The variance is a measure of the "spread" of a distribution, often denoted by $\sigma^2$. 
- This is defined as follows: $\int (x-\mu )^2p(x) \, dx$
- The standard deviation is defined as the square root of the variance, or $\sigma$. 
#### Mode of a distribution
- The mode of a distribution is the value with the highest probability mass or probability density: $x* = agmax_{x}~p(x)$
- If the distribution is multimodal, this may not be unique
## Bayes' Rule
* Inference- the act of passing from sample data to generalizations, usually with calculated degrees of certainty. 
* The term Bayesian is used to refer to inference methods that represent degrees of certainty using probability theory, and which leverage Bayes' rule, to update the degree of certainty given data. 
* Bayes' rule is just a formula for computing the probability distribution over possible values of an unknown quantity $H$ given some observed data $Y=y$: $p(H=h |Y=y)=\frac{P(H=h)p(Y=y|H=h)}{p(Y=y)}$. 
* This follows automatically from the identity $p(h|y)p(y)=p(h)p(y|h)=p(h, y)$ which itself follows from the product rule of probability.
* The term $p(H)$ represents what we know about possible values of $H$ before we see any data; this is called the prior distribution. 
* If $H$ has $K$ possible values, then $p(H)$ is a vector of $K$ probabilities, that sum to $1$. 
* The term $p(Y|H=h)$ represents the distribution over the possible outcomes $Y$ we expect to see if $H=h$; this is called the observation distribution. 
* When we evaluate this at a point corresponding to the actual observations, $y$, we get the function $P(Y = y| H = h)$, which is called the likelihood. This is a function of $h$, since $y$ is fixed. 
* Multiplying the prior distribution $p(H=h)$ by the likelihood function $p(Y=h|H=h)$ for each $h$ gives the unnormalized joint distribution $p(H=h, Y=y)$.  We can convert this into a normalized distribution by dividing by $p(Y=y)$, which is known as the marginal likelihood, since it is computed by marginalizing over the unknown $H$: 
	* $p(Y=y)=\sum_{h' \in H}p(H=h')p(Y=y|H=h')=\sum_{h' \in H}P(H=h', Y=y)$
* Normalizing the joint distribution by computing $\frac{p(H=h, Y=y)}{p(Y=y)}$ for each h gives the posterior distribution $p(H=h|Y=y)$ which represents our new belief state about the possible values of $H$. 
* We can summarize Bayes rule in words as follows: the posterior distribution is proportional the prior probability times the likelihood. 
* Using Bayes rule to update a distribution over unknown values of some quantity of interest, given relevant observed data is called Bayesian inference, probabilistic inference, or posterior inference. 
### Inverse Problems
- By contrast of probability theory which is concerned with predicting a distribution over outcomes $y$ given knowledge or assumptions about the state of the world $h$, inverse probability is concerned with inferring the state of the world from observations of outcomes. 
- We can thing of this as inverting the $h \to y$ mapping. 
- To tackle such inverse problems, we can use Bayes' rule to compute the posterior, $p(h|y)$, which gives a distribution over possible states of the world. 
## Bernoulli and Binomial Distributions
- The Bernoulli distribution is used to model binary events. 
### Definition
* Consider tossing a coin, where the probability of event that it lands heads is given by $0 \leq \theta\leq 1$. Let $Y=1$ denote this event, and let $Y=0$ denote the event that it lands tails. Thus we are assuming the Bernoulli distribution: $p(Y=1)=\theta$, $p(Y=0)=1-\theta$. 
* The probability mass function of this distribution is defined as follows: $Ber(y|\theta)=\begin{cases} 1-\theta & \text{if y =0}\\ \theta &\text{ if y=1 }\end{cases}$ 
* We can write this in  a more concise manner as follows: $Ber(y|\theta)=\theta^y(1-\theta)^{1-y}$. 
### Sigmoid Function
- When we want to predict a binary variable $y \in \{0,1\}$ given some inputs $x \in X$, we need to use a conditional probability distribution of the form $p(y|x, \theta)=Ber(y|f(x; \theta))$ where $f(x;\theta)$ is some function that predicts the mean parameter of the output distribution. 
- To avoid the requirement that $0\leq f(x;\theta)\leq 1$, we an let $f$ be an unconstrained function, and use the following model: $p(y|x, \theta)=Ber(y|\sigma(f(x;\theta)))$ where $\sigma()$ is the sigmoid or logistic function defined as follows: $\sigma(a)=\frac{1}{1+e^{-a}}= \frac{e^{a}}{1+e^{a}}$. 
- The sigmoid function maps the whole real line to $[0,1]$, which is necessary for the out put to be interpreted as a probability, and hence a valid value for the Bernoulli parameter $\theta$. 
## Univariate Gaussian (Normal) Distribution
- The most widely used distribution of real-valued random variables $y \in \mathbb{R}$ is the Gaussian distribution, also called the normal distribution.
### Cumulative Distribution Function
* The CDF of the Gaussian is defined by: $\int _{-\infty}^y\mathbf{N(z|\mu, \sigma^{2)} \, dx=\frac{1}{2}}\left[ 1+error\left( \frac{z}{\sqrt{ 2 }} \right) \right]$, where $z=\frac{y-\mu}{\sigma}$ . 
* The parameter $\mu$ encodes the mean of the distribution, which is the same as the mode, since the distribution is unimodal. 
* The parameter $\sigma^2$ encodes the variance. 
* Sometimes we talk about the precision of the Gaussian, which is the inverse variance, denoted $\lambda=\frac{1}{\sigma^2}$. 
* When $\mu=o$ and $\sigma=1$, the Gaussian is called the standard normal distribution. 