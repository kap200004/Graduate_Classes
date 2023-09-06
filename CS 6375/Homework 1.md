**Question 1:** As a consultant to a local plant that manufactures usb drives you need to estimate the failure probability of their usb drives. In order to do that, a series of experiments is performed; in each experiment several usb drives are tried until a good one is found. The number of failures, $k$, is recorded. 
	- Given that $p$ is the failure probability, what is the probability of $k$ failures before a good usb drive is found? 
	- **Answer:** $p^k(1-p)$
	- You have performed m independent experiments of this form, recording, $k_{1}, k_{2}, \dots, k_{m}$. Estimate the most likely value of $p$ as a function of $m$ and $k_{1}, k_{2}, \dots, k_{m}$. 
	-  **Answer:** 
	- $p(\mathbf{D}|p)=\Pi_{i=1}^mp^{k_{i}}(1-p)$  
	- $L(p(\mathbf{D}|p))=\sum_{i=1}^mk_{i}\log(p)+\log(1-p)$
	- $L(p(\mathbf{D}|p)) \frac{d}{dp} \equiv  \frac{\sum_{i=1}^{m}k_{i}}{p}-\frac{m}{1-p}$  
	- $\text{let }M = \sum_{i=1}^{m}k_{i}$
	- $\frac{M}{p}=\frac{m}{1-p}\equiv M-Mp=mp\equiv M=Mp+mp\equiv M=p(M+m)\equiv p=\frac{M}{M+m}\equiv \frac{\sum_{i=1}^{m}k_{i}}{\sum_{i=1}^{m}k_{i}+m}$
**Question 2:** Let $\theta$ be the probability that "Thumbtack 1" shows heads and $2\theta$ be the probability that "Thumbtack 2" shows heads. you are given the following dataset.

|T1|T2|T1|T1|T2|T2|
|--|--|--|--|--|--|
| Tails | Heads | Tails | Tails | Heads | Heads

- What is the likelihood of the data given $\theta$?
	- $p(D|\theta)=(1-\theta)^{3}(2\theta)^3$ 
- What is the maximum likelihood estimate of $\theta$?
	- $LL(p(\mathcal{D}|\theta))=3\log(1-\theta)+3\log(2\theta)$
	- $LL(p(D|\theta)) \frac{d}{d \theta}= -\frac{3}{1-\theta}+\frac{6}{2\theta}$
	- $-6\theta+6-6\theta=0\equiv 12\theta=6$
	- $\theta=.5$

**Question 3:** Write down the expression for the log-likelihood of the data and then derive the expression for the maximum likelihood estimates for the following two distributions. 
- Categorical distribution defined over the support $\{1, ..., k\}$ (namely $x$ is a discrete variable and can take $k$ values); find an expression for the MLE of the parameters $\theta_{1}, \dots \theta_{k} \text{ s.t. } \theta_{i} \geq 0, \text{ and } \sum^{k}_{i=1}\theta_{i}-1$. 