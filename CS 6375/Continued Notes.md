## Categorical and Multinomial Distributions
- To represent a distribution over a finite set of labels, $y \in \{1, \dots,C\}$, we can use the categorical distribution, which generalizes the Bernoulli to $C>2$ values. 
### Definition
- The categorical distribution is a discrete probability distribution with one parameter per class: $Cat(y|\boldsymbol{\theta})=\Pi^{C}_{c=1}\theta_{c}^{\mathbb{I}(y=c)}$
- In other words, $p(y=c|\theta)=\theta_{c}$. Note that the parameters are constrained so that $0\leq \theta_{c}\leq 1$ and $\sum_{c=1}^{C}\theta_{c}=1$. 
- We can write the categorical distribution in another way by converting the discrete variable $y$ into a one-hot-vector with $C$ elements, all of which are 0 except for the entry corresponding to the class label. 
- Using the one-hot encodings, we can write the categorical distribution as follows: $Cat(\boldsymbol{y}|\boldsymbol{\theta})=\Pi^{C}_{c=1}\theta_{c}^{y_{c}}$.
- The categorical distribution is a special case of the multinomial distribution. 
- Think of rolling a $C$-sided dice $N$ times. Let us define $\boldsymbol{s}$ to be a vector that counts the number of times each face shows up, i.e. $s_{c}=\sum^{N}_{n=1}\mathbb{I}(y_{n}=c)$. The distribution of $\mathbf{s}$ is given by the multinomial distribution: $Mu(\mathbf{s}|N, \boldsymbol{\theta})={{N}\choose{s_{1}, \dots, s_{c}}} \Pi^{C}_{c=1}\theta_{c}^{s_{c}}$ where $\theta_{c}$ is the probability that side c shows up and $N! \choose s_{1}, \dots, s_{c}$ is the multinomial coefficient, which is the number of ways to divide a set of size $N$ into subsets with sizes $s_{1}$ up to $s_{c}$. If $N=1$, the multinomial distribution becomes the categorical distribution. 
### Softmax Function
- In the conditional case, we can define $p(y|\boldsymbol{x,\theta})=Cat(y|f(\boldsymbol{x,\theta}))$ and we require that $0 \leq f_{c}(\boldsymbol{x; \theta})\leq 1$, and $\sum^{c}_{c=1}f_{c}(\boldsymbol{x;\theta})=1$. 
- To avoid the requirement that $f$ directly predict a probability vector, it is common to pass the output from $f$ into the softmax function, also called the multinomial logit. This is defined as follows: $\boldsymbol{S(a)}=\left[ \frac{e^{a_{1}}}{\sum^{C}_{c'=1}e^{a_{c'}}} , \dots, \frac{e^{a_{C}}}{\sum^{C}_{c'=1}e^{a_{c'}}} \right]$. This maps $\mathbb{R}^{C}$ to $[0,1]^{C}$, and satisfies the constraints $0 \leq \boldsymbol{S(\alpha)_{c}}\leq 1$, and $\sum^{c}_{c=1}\boldsymbol{S(a)_{c}}=1$. 
- The inputs to the softmax are $a=f(\boldsymbol{x;\theta})$, also called logits, and are a generalization of the log odds. 
### Multiclass Logistic Regression
- If we use a linear predictor of the form $f(\boldsymbol{x;\theta})= \boldsymbol{Wx+b}$, where $\boldsymbol W$ is a $C\times D$ matrix, and $b$ is a $C$-dimensional bias vector, the final model becomes $p(y|\boldsymbol{x; \theta})= Cat(y|\boldsymbol{S(Wx+b)})$. 
- Let $\boldsymbol{a=Wx+b}$ be the $C$-dimensional vector of logits. Then we can rewrite the above as follows: $p(y=c|\boldsymbol{x;\theta})= \frac{e^{a_{c}}}{\sum^{C}_{c'}e^{a_{c'}}}$. This is known as multinomial logistic regression. 
- If we have just two classes, this reduces to binary logistic regression. To see this, note that $\boldsymbol{S(a)_{0}}=\frac{e^{a_{0}}}{e^{a_{0}}+e^{a_{1}}}= \frac{1}{1+e^{a_{1}-a_{0}}}$, so we can just train the model to predict $a=a_{1}-a_{0}$. 
### Log-Sum Exponent Trick