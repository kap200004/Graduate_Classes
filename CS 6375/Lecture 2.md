* A third view: Learning is just a combination of three things, a representation of a function, and evaluation method, and an optimization method for optimizing our function. 
	* Every Machine Learning method or algorithm is just a combination of these three things. Representation gives you the hypothesis class. 
### Probabilistic Modeling and Maximum Likelihood Estimation
Univariate Probabilistic Model:
**Given:** A dataset having *N* i.i.d. samples and one binary feature *X* that can take two values from {0, 1}. Find P(X=1). 
* Assume that each point in the dataset $D$ is generated from a Bernoulli distribution having parameter $\theta$. 
* $P(X=1)=\frac{\alpha_{1}}{N}=\frac{\alpha_{1}}{\alpha_{0}+\alpha_{1}}$. 
* **General Formula:** $P(X=1|\theta)=\theta$ or more generally, $P(X=x|\theta)=\theta^{x}(1-\theta)^{1-x}$. 
* **The Likelihood of the Dataset**: The probability of generating the dataset. Since all points in the dataset are independent and identically distributed. $P(D|\theta)=P(x^{1},\dots,x^{n}= \Pi^{n}_{i=1}P(x^{i}|\theta)$. 
* Maximum Likelihood Estimate: Find a value for $\theta$ such that the likelihood is maximized, i.e. $\theta_{mle}=arg max_{\theta}P(D|\theta)$. We optimize by taking the derivative and setting it to zero. 
* Take the time to prove that $\theta_{mle}=\frac{\alpha_{1}}{\alpha_{0}+\alpha_{1}}$. Optimize using the log-likelihood. Derive from both as a homework. 

