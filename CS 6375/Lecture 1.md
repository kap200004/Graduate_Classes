- Learning- the ability to perform a task in a situation which has never been encountered before. e.g. Learning = Generalization.
- Supervised Learning: The training data includes desired outputs. 
- Unsupervised Learning: Training data does not include outputs, find hidden/interesting structure in data. 
- Semi-supervised learning- Training data includes a few desired outputs. 
- Reinforcement learning- the learner interacts with the world via actions, and tries to find an optimal policy of behavior with respect to "rewards" it receives from the environment. 
- Classification-outputs are discrete, Regression- desired outputs are continuous. 
### Introduction to Supervised Learning
* Induction- is defined as the process of reasoning which infers a general conclusion based on individual cases. 
	* Differs from deduction where a knowledge base is given and you are answering specific queries using the knowledge base. 
#### Classification and Regression
* Classification: $y = f(x)$ is a discrete quantity. 
* Regression: $y = f(x)$ is a continuous quantity. 
* A more Plausible approach to selecting h:
	* Select a hypothesis class H. This models the assumptions you make about the function f. 
	* Find a function $h \in \mathbb{H}$ that is consistent with the given data based on some evaluation criteria.
* Two views of learning:
	* Learning requires guessing a good, small hypothesis class via step 1. 
	* Learning is removal of our remaining uncertainty, via step 2. 

* There are $2^{2^n}$ possible Boolean functions over $n$ features. Why? There are $2^n$ possible assignments and a function evaluates each of them to  be either true or false.  