## Bayesian Concept Learning
- The subset of $\mathcal{H}$ that is consistent with the data $D$ is called the version space. 
### Likelihood 
- Let us assume that examples are sampled uniformly at random from the extension of a concept which is the set of elements that belong to the concept. This assumption is called the strong sampling assumption. 
- Given this assumption, the probability of independently sampling $N$ items (with replacement) from $h$ is given by $p(D|h) = \frac{1}{|h|}^N$. 
- This is called the size principle, which means the model favors the simplest or smallest hypothesis consistent with the data. This is more commonly known as Occam's razor. 
### Prior
- The prior is the mechanism by which background knowledge can be brought to bear on a problem. Without this, rapid learning, i.e. from a small sampling size is impossible. 
### Posterior
- The posterior is simply the likelihood times the prior, normalized. In this contact we have the posterior $p(h|D)= \frac{p(D|h)p(h)}{\sum_{h' \in H}p(D, h')}$. 
- In general, when we have enough data, the posterior $p(h|D)$ becomes peaked on a single concept, namely the MAP estimate, i.e., $p(h|D) \to \delta_{h}MAP(h)$ where $h^{MAP} = argmax_{h}p(h|D)$ is the posterior mode, and where $\delta$ is the Dirac measure defined by $\delta_{x}(A)= 1$ if $x \in A$. 
- Note that the MAP estimate can be written as $h^{MAP}=argmax_{h}p(D|h)p(h)=argmax_{h}[\log p(D|h)+\log p(h)]$. 
- Since the likelihood term depends exponentially on $N$, and the prior stays constant, as we get more and more data, the MAP estimate converges towards the maximum likelihood estimate or $MLE=argmax(p(D|h))=argmax_{h}\log p(D|h)$, in other words, if we have enough data, we see that the data overwhelms the prior.
- If the true hypothesis is in the hypothesis space, then the MAP/ML estimate will converge upon this hypothesis.
- We also say that the hypothesis space is identifiable in the limit, meaning we can recover the truth in the limit of infinite data. 
- If our hypothesis class is not rich enough to represent the truth, we will converge on the hypothesis that is as close as possible to the truth. 
### Posterior Predictive Distribution
- The posterior is our internal belief state about the world. The way to test if our beliefs are justified is to use them to predict objectively observable quantities. 
- Specifically the posterior predictive distribution in this context is given by $p(x \in C|\mathcal{D})=\sum_{h}p(y=1|x, h)p(h|\mathcal{D})$. This is just a weighted average of the predictions of each individual hypothesis and is called Bayes model averaging. 
- When we have a small and/or ambiguous dataset, the posterior $p(h|D)$ is vague, which induces a broad predictive distribution, however as the the dataset grows, the posterior becomes a delta function centered at the MAP estimate. 
## The Beta-Binomial Model
- In many applications, the unknown parameters of a model are continuous, so the hypothesis space is (some subset) or $\mathbb{R}^K$ where $K$ is the number of parameters. 
- This complicates the mathematics, since we have to replace sums with integrals, however, the basic ideas are the same. 
- When inferring a distribution over a random variable, we follow a familiar recipe of specifying the likelihood and prior, and deriving the posterior and posterior predictive. 
### Likelihood
- Suppose we have $X_{i} = Ber(\theta)$, where $X_{i}=1$ represents "heads", and $\theta \in [0,1]$ is the rate parameter (probability of heads). 
- If the data are iid, the likelihood has the form $p(D|\theta)=\theta^{N_{1}}(1-\theta)^{N_{0}}$. 
- We have $N_{1}=\sum_{i=1}^{N}\mathbb{I}(x_{i}=1)$ where $\mathbb{I}$ means we add 1 if $x_{i}=1$ is true, and 0 otherwise. These two counts ($N_{1}, N_{0}$) are called the sufficient statistics of the data, since this is all we need to know about $D$ to infer $\theta$ .
### Prior
- At this point, we need a prior which has support over the interval $[0,1]$. To make the math easier, it would be convenient if the prior had the same form as the likelihood, i.e. in the case of a Bernoulli likelihood: $p(\theta)=\theta^{\gamma 1}(1-\theta)^{\gamma 2}$ for some prior parameters $\gamma 1$ and $\gamma 2$. 
- If this is the case, then we could easily evaluate the posterior by simply adding up the exponents. 
- When the prior and the posterior have the same form, we say that the prior is a conjugate prior for the corresponding likelihood. 
- In the case of the Bernoulli, the conjugate prior is the beta distribution: $\beta(\theta|a, b)= \theta^{a-1}(1-\theta)^{b-1}$. 
- The parameters of the prior are called hyper-parameters, and we can set them in order to encode our prior beliefs. If we know nothing about $\theta$, except that it lies in the interval $[0,1]$, we can use a uniform prior, which is a kind of uninformative prior. The uniform distribution can e represented by a  beta distribution with $a=b=1$. 
### Posterior
- If we multiply the likelihood by the beta prior we get the following posterior: $p(\theta|D)=Ber(N_{1}|\theta, N_{0}+N_{1})B e t a(\theta|a, b)= Be t a(\theta|N_{1}+a, N_{0}+b)$
- In particular, the posterior is obtained by adding the prior hyper-parameters to the empirical counts. For this reason, the hyper-parameters are known as pseudo counts. 
#### Posterior Mean and Mode
- The MAP estimate is given by $\frac{a+N_{1}-1}{a+N_{1}+N_{2}+b-2}$, but if we use a uniform prior, the the MAP estimate reduces to the MLE, which is just the empirical fraction of heads: $mle = \frac{N_{1}}{N_{1}+N_{2}}$ . 
#### Overfitting and the Black Swan Paradox
- Unfortunately, when we use the MLE to fit our model, it can perform quite poorly when the sample size is small. In fact, if a positive sample has not been seen, the MLE will be 0 since this makes the observed data as probable as possible. 
  - This is known as the zero count problem, but we can derive a simple Bayesian solution to the problem. We will use a uniform prior, so $a=b=1$. In this case, plugging in the posterior mean gives Laplace's rule of succession: $p(x=1|D)=\frac{N_{1}+1}{N_{1}+N_{0}+2}$
  - This justifies the common practice of adding 1 to empirical counts, normalizing and then plugging them in, a technique known as add-one smoothing. 
- 1-Laplace smoothing is where we pretend we saw every possible outcome once. 
## Naive Bayes Classifiers
- In this section, we discuss how to classify vectors of discrete-valued features, $x \in \{1, \dots K\}^D$, where $K$ is the number of values for each feature and $D$ is the number of features. 
- This requires us to specify the class-conditional distribution $p(x|y=c)$. 
- This simplest approach is to assume the features are conditionally independent given the class label. This allows us to write the class-conditional density as a product of one-dimensional densities: $p(x|y=c, \theta)=\Pi^{D}_{j=1}p(x_{j}|y=c, \theta_{jc})$. 
- The resulting model is called a naive Bayes classifier. Even if the naive assumption that the features are not independent conditioned on the class, it often works well anyway. 
### Model Fitting 
- Training a naive Bayes classifier usually means computing the MLE or the MAP estimate for the parameters. 
