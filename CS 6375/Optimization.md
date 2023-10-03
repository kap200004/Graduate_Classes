## Introduction
- The core problem in machine learning is parameter estimation, also known as model fitting. This requires solving an optimization problem where we try to find the values for a set of variables $\theta \in \Theta$, that minimize a scalar-valued loss function: $\theta^{*}=argmin \mathcal{L}(\theta)$. 
- If we want to *maximize* a score function or reward function $R(\theta)$, we can equivalently minimize $L(\theta)=-R(\theta)$. 
- An algorithm that can find an optimum of an objective function is often called a solver. 
### Local Vs Global Optimization
- A point that satisfies our equation for $\theta^{*}$ is called a global optimum. Finding such a point is called global optimization. 
- Generally, finding a global optima is computationally intractable, so we try to find a local optimum which is a point $\theta^{*}$ that has lower (or equal) cost than "nearby" points. 
- A local minimum could be surrounded by other local minima with he same objective value. This is called a flat local minimum. A point is said to be a strict local minimum if its cost is strictly lower than those of neighboring points. 
- If an algorithm is guaranteed to converge to a stationary point from any starting point, it is called globally convergent. However, this does not mean (rather confusingly) that it will converge to a global optimum, it just means it will converge to some stationary point. 
#### Optimality Conditions for Local vs Global Optima
- For continuous, twice differentiable functions, we can precisely characterize the points which correspond to local minima. 
- The gradient of a function at a point $x$ is the vector if its partial derivatives: $\boldsymbol{g}= \frac{\delta f}{\delta \boldsymbol{x}}=\nabla f= \begin{matrix} \frac{\delta f}{\delta x_{1}}\\\cdots\\ \frac{\delta f}{\delta xn}\end{matrix}$
- We see that the $\nabla$ operator maps a function $f:\mathbb{R}^{n} \to \mathbb{R}$ to another function $g: \mathbb{R}^{d} \to \mathbb{R}^{d}$. 
- Let $g(\theta)=\nabla L(\theta)$ be the gradient vector, and $\boldsymbol{H(\theta)= \nabla^{2}L(\theta)}$ be the Hessian matrix. Consider a point $\theta^{*} \in \mathbb{R}^{D}$, and let $g^{*}=g(\theta)$ be the gradient at that point, and $H^{*}=H(\theta)$ be the corresponding Hessian. One can show that the following conditions characterize every local minimum:
	- If $\theta^{*}$ is a local minimum, then we must have $g^{*}=0$ (i.e., $\theta^{*}$ must be a stationary point), and $H^{*}$ must be positive semi-definite. 
	- Sufficient condition: If $g^{*}=0$ and $H^{*}$ is positive definite, then $\theta^{*}$ is a local optimum. 
### Descent Direction
- We say that a direction $d$ is a descent direction if there is a small enough (but nonzero) amount $\alpha$ we can move in direction $d$ and be guaranteed to decrease the function value. Formally, we require that there exists an $\alpha_{max}$ > 0  such that $\mathcal{L}(\theta+\alpha \boldsymbol{d}) < \mathcal{L}(\theta)$. 
- The gradient of our loss function points in the direction of maximal increase in $f$, so the negative gradient is a descent direction. 
- Let $d =-g$ our weight update rule becomes $w_{i} = w_{i}+\alpha d_{i}$ where alpha is some multiplier that we use to take smaller steps in descent. 
