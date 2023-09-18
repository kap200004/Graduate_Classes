# Generative Vs Linear Classifiers
## Gaussian Naive Bayes vs Logistic Regression
- Logistic regression is discriminative rather than generative because with it we are learning $p(y|x)$ where as Naive Bayes maximizes and learns $p(x|y)$ and is therefore able to generate data. 
- When the assumptions of independence are not correct, logistic regression is less biased because it does not assume conditional independence. Therefore logistic regression is expected to outperform Gaussian Naive Bayes. However when the variables are conditionally independent, GNB and LR produce identical classifiers and GNB is less computationally complex. (Under the assumption we have a large amount of data). 
- Non-asymptotic analysis- how fast does it take converge to a true value? GNB converges with O(log n) samples, while logistic regression needs O(n) samples. 
- NG and Jordan 2002. 
- When do you use generative models?
	- When we can make the assumptions that our data is conditionally independent given the classification. 
	- We have a large amount of data or a small amount of data we will use GFN. 
	- For this we maximize the log likelihood. 
- When do we use discriminative
	- When our conditional independence given $y$ is not correct. 
	- We have a medium size amount of data. 

Matrix of discriminative vs generative use:

|     | Small | Medium | Large |
|---|----|----|-----|
|Assumptions are correct | Generative | Generative | Generative |
|Assumptions are not correct | Generative | Discriminative | Generative |


## Neural Networks and Back Propagation
- When the number of features (dimensions) is larger than the number of examples, linear classifiers work very well. 
- Linear classifiers have limited expressive power, in practice, most datasets will need non-linear classifiers. 
- How do we build nonlinear classifiers from linear classifiers?
	- Build a network of linear classifiers. 
	- Construct a feed-forward network of linear classifiers. 
	- input layer are the features of the data. 
	- Hidden layers are linear classifiers with output nodes of nodes in the previous layer.
	- Output layer- Desired output node, output of nodes in the hidden layer a level below as input. 
	- We must use an activation function in each of our hidden nodes, that is nonlinear. This is what allows us to get a nonlinear classifier. 
- Assume that each hidden node and output node is a sigmoid unit. $o = \sigma\left( \sum^{n}_{i=1} w_{o,i}h_{i} \right)$
- Nonlinearity must be used at the hidden nodes, you can't just use a nonlinear function at the output. Otherwise our neural network is nothing but a linear classifier. 
- Typically we call our nonlinear functions activation functions: sigmoid, linear, sign, tanh, relu. 

