**Question 1:** For each of the following three datasets, write 'Yes' if logistic regression will have zero training error on the dataset. Otherwise write 'No'. If your answer is Yes draw a decision boundary. Explain why in one sentence or less if your answer is No. 
1. This is not linearly separable, so there will be error using logistic regression, or worse it will not converge. 
2. ![[1000003375.jpg]]
3. This is not linearly separable, so there will be error using logistic regression, or worse it will not converge. 
**Question 2:** Consider a regression problem ($x,y$ are continuous variables) given by $y=w_{1}x+w_{0}$, with a training set having $m$ examples ($x_{1}, y_{1}$), ..., $(x_{m},y_{m})$. Suppose that we wish to minimize the mean *fifth* degree error (loss function) given by: $Loss=\frac{1}{m} \sum^{m}_{i=1}(y_{i}-w_{1}x_{i}-w_{0})^5$

1. Calculate the gradient with respect to the parameters $w_{1}$ and $w_{0}$. 
   
   Let $u=y_{i}-w_{1}x_{i}-w_{0}$. $Loss=\frac{1}{m}\sum^{m}_{i=1}u^{5}$, $\frac{\delta}{\delta u}=5u^{4}$, $\frac{\delta u}{dw_{0}}=-1$, $g_{0} = -\frac{5}{m} \sum^{m}_{i=1}(y_{i}-w_{1}x_{i}-w_{0})^4$, $\frac{\delta u}{dw_{1}}= -x_{i}$, $g_{1}=-\frac{5}{m}\sum^{m}_{i=1}x_{i}(y_{i}-w_{1}x_{i}-w_{0})^4$. 
   $\nabla_{loss}= \begin{pmatrix}-\frac{5}{m} \sum^{m}_{i=1}(y_{i}-w_{1}x_{i}-w_{0})^{4}\\ -\frac{5}{m}\sum^{m}_{i=1}x_{i}(y_{i}-w_{1}x_{i}-w_{0})^4\end{pmatrix}$
2. Write down the pseudo-code for stochastic (also called online) gradient descent for this problem. 
```python
def stochastic_gradient_descent(X, Y, weights): #X and Y are the data and label vectors respectively. Weights have previously been randomly selected. 
	prev_loss = 0
	new_loss = 1
	alpha = .001
	decay_rate = .9
	
	while new_loss - prev_loss > .00001:
		prev_loss = new_loss
		index = rand.randint(0, len(data))
		rand_X = X[index]
		rand_Y = Y[index]
		del_zero = alpha*5*(rand_Y-weights[1]*rand_X-weights[0])
		del_one = rand_X*del_zero
		weights[0] += del_zero
		weidhts[1] += del_one
		alpha *= decay_rate
		new_loss = 0
		for i in range(len(X)):
			new_loss += (Y[i]-weights[1]*X[i]-weights[0])**5
		newloss /= len(X)
```

**Question 3:** What is the time and space complexity of the (batch) gradient ascent procedure used for logistic regression. Assume that the number of examples (data points) is $d$, maximum number of iterations is $s$, and the number of features is $n$.

To calculate the gradient, we must run through the data doing a constant time calculation on n features. This is $O(nd)$, if we run this for $s$ iterations our complexity is $O(snd)$. The space complexity is simply our data which is $O(nd)$.

**Question 4:**
Show that two-class Gaussian Naïve Bayes with class independent variables is a linear classifier. Recall that a linear classifier or a linear threshold function is a method that uses the following classification rule: 
	Classify as 1 if $w_{0}+\sum^{n}_{i=1}w_{i}x_{i}>0$
Use the following notation for two-class Gaussian Naïve Bayes with class independent variables: 
- Class Priors: $P(Y=1)= \theta; P(Y=0)=1-\theta$

We have for the Gaussian Naïve Bayes, the capability to classify as 1 if $\frac{P(Y=1|x_{i})}{ P(Y=0|x_{i})} > 1$. Naive Bayes allows us to write this as $\frac{\frac{P(x_{i}|Y=1)P(Y=1)}{P(x_{i})}}{\frac{P(x_{i}|Y=0)P(y=0)}{P(x_{i})}}= \frac{p(x_{i}|Y=1)P(Y=1)}{P(x_{i|Y=0})P(Y=0)}$.  So we are given using Naïve Bayes to classify as 1 if $\frac{p(x_{i}|Y=1)P(Y=1)}{P(x_{i|Y=0})P(Y=0)} > 1$. Plugging in our formula for Gaussian distribution we get $p(x_{i}|Y=1)P(Y=1)= \theta\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}(\frac{x_{i}-\mu_{i,1}}{\sigma^{2}_{i}})^{2}} \right)$ and $p(x_{i}|Y=0)P(Y=0)= (1-\theta)\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}(\frac{x_{i}-\mu_{i,0}}{\sigma^{2}_{i}})^{2}} \right)$ so we get the rule classify as 1 if $\frac{\theta\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}\left( \frac{x_{i}-\mu_{i,1}}{\sigma^{2}_{i}} \right)^{2}} \right)}{(1-\theta)\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}(\frac{x_{i}-\mu_{i,0}}{\sigma^{2}_{i}})^{2}} \right)} > 1$. The first thing we will do is take the log of both sides to simplify and we get $\ln \theta\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}\left(\frac{x_{i}-\mu_{i,1}}{\sigma^{2}_{i}}\right)^{2}} \right)- \ln (1-\theta)\left( \frac{1}{\sigma \sqrt{ 2\pi }}e^{\frac{-1}{2}(\frac{x_{i}-\mu_{i,0}}{\sigma^{2}_{i}})^{2}} \right)>\ln 1$. We simplify more to get $\ln \theta + \ln \frac{1}{\sigma \sqrt{ 2\pi }}+\ln e^{\frac{-1}{2}\left(\frac{x_{i}-\mu_{i,1}}{\sigma^{2}_{i}}\right)^{2}}-[\ln(1-\theta)+\ln \frac{1}{\sigma \sqrt{ 2\pi }}+\ln e^{\frac{-1}{2}(\frac{x_{i}-\mu_{i,0}}{\sigma^{2}_{i}})^{2}}]$ which we can simplify even further to $\ln \frac{\theta}{1-\theta}+-\frac{1}{2}[\frac{(x_{i}-\mu_{i,0})^2-(x_{i}-\mu_{i,1})^2}{\sigma^{2}_{i}}]$ $= \ln \frac{\theta}{1-\theta}+ -\frac{1}{2}[\frac{x_{i}^{2}-2x_{i}\mu_{i,1}+\mu^{2}_{i,1}-x_{i}^{2}+2x_{i}\mu_{i,0}-\mu_{i,0}^{2}}{\sigma^{2}_{i}}]$ $= \ln \frac{\theta}{1-\theta}+\frac{\mu_{i,1}^{2}-\mu^{2}_{i,0}}{2\sigma^{2}_{i}}+x_{i}\frac{\mu_{i,1}-\mu_{i,0}}{\sigma^{2}_{i}}$. Because each of our $x_{i}$ are independent of each other given $y$ we have classify as 1 if $\ln \frac{\theta}{1-\theta}+\sum^{n}_{i=1}\frac{\mu_{i,1}^{2}-\mu^{2}_{i,0}}{2\sigma^{2}_{i}} + \sum^{n}_{i=1}x_{i}\frac{\mu_{i,1}-\mu_{i,0}}{\sigma^{2}_{i}} > 0$. 
Let $w_{0}=\ln \frac{\theta}{1-\theta}+\sum^{n}_{i=1}\frac{\mu_{i,1}^{2}-\mu^{2}_{i,0}}{2\sigma^{2}_{i}}$ and $w_{i} = \frac{\mu_{i,1}-\mu_{i,0}}{\sigma^{2}_{i}}$. We  have that classify as 1 if $w_{0}+\sum^{n}_{i=1}w_{i}x_{i}>0$ which is simply a linear classifier with chosen weights. 