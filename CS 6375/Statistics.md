- The process of estimating $\boldsymbol{\theta}$ from $\mathcal{D}$ is called model fitting, or training, and is at the heart of machine learning. 
- There are many methods for producing such estimates, but most boil down to an optimization problem of the form: $\hat{\boldsymbol{\theta}}=argmin~ \mathcal{L}(\boldsymbol{\theta})$ where $\mathcal{L}(\boldsymbol{\theta})$ is some kind of loss function or objective function. 
- In statistics, the process of quantifying uncertainty about an unknown quantity estimated from a finite sample of data is called inference. 
## Maximum Likelihood Estimation
- The most common approach to parameter estimation is to pick the parameters that assign the highest probability to the training data; this is called maximum likelihood estimation or MLE. 
### Definition
- We define MLE as follows: $\hat{\boldsymbol{\theta}}_{mle}=argmax_{\theta}p(\mathcal{D}|\boldsymbol{\theta})$. 
- We usually assume the training examples are independently sampled from the same distribution, so the (conditional) likelihood becomes $p(D|\boldsymbol{\theta})=\Pi^{N}_{n=1}p(\boldsymbol{y_{n}|x_{n},\theta})$. This is known as the independent and identically distributed assumption. 
- We usually work with the log likelihood, which is given by $L L(\boldsymbol{\theta})=\log p(D|\boldsymbol{\theta})= \sum^{N}_{n=1}\log p(\boldsymbol{y_{n}|x_{n, \theta}})$. 
### Justification
- Suppose we approximate the posterior by a delta function, $P(\boldsymbol{\theta}|D)= \delta(\boldsymbol{\theta-\theta_{map}})$, where $\theta_{map}$ is the posterior mode, given by $\theta_{map}=argmax_{\boldsymbol{\theta}}\log p(\boldsymbol{\theta|D})=argmax_{\boldsymbol{\theta}}\log p(D|\boldsymbol{\theta})+\log p(\boldsymbol{\theta})$. 
- If we use a uniform prior, the MAP estimate becomes equal to the MLE. 
### MLE for the Bernoulli Distribution
- The negative log likelihood for the Bernoulli distribution is given by: 
  $NL L(\theta)= -\log \Pi^{N}_{n=1}p(y_{n}|\theta)$
  $\equiv -\log \Pi^{N}_{n=1}\theta^{\mathbb{I}(y_{n}=1)}(1-\theta)^{\mathbb{I}(y_{n}=0)}$
  $\equiv -\sum^{N}_{n=1}\mathbb{I}(y_{n}=1)\log \theta+\mathbb{I}(y_{n}=0)\log(1-\theta)$
  $\equiv -[N_{1}\log \theta+N_{0}\log(1-\theta)]$
- The total count, $N=N_{0}+N_{1}$, is called the sample size and $N_{0}$ and $N_{1}$ are called the sufficient statistics of the data, since they summarize everything we need to know about $\mathcal{D}$. 
- The MLE can be found by solving $\frac{d}{d \theta}NL L(\theta)=0$. The derivative of the NLL is $\frac{d}{d \theta}NL L(\theta)= -\frac{N_{1}}{ \theta}+\frac{N_{0}}{ 1-\theta}$ and hence the MLE is given by $\theta_{mle}= \frac{N_{1}}{ N_{0}+N_{1}}$ which is just the empirical fraction of heads, which is an intuitive result. 
### MLE for the Categorical Distribution
- To compute the MLE for the categorical distribution, we have to minimize the NLL subject to the constraint that $\sum^{K}_{k=1}\theta_{k}=1$. To do this, we can use the method of Lagrange multipliers.   