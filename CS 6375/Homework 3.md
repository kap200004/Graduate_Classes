**Question 1:** For each of the following three datasets, write 'Yes' if logistic regression will have zero training error on the dataset. Otherwise write 'No'. If your answer is Yes draw a decision boundary. Explain why in one sentence or less if your answer is No. 

**Question 2:** Consider a regression problem ($x,y$ are continuous variables) given by $y=w_{1}x+w_{0}$, with a training set having $m$ examples ($x_{1}, y_{1}$), ..., $(x_{m},y_{m})$. Suppose that we wish to minimize the mean *fifth* degree error (loss function) given by: $Loss=\frac{1}{m} \sum^{m}_{i=1}(y_{i}-w_{1}x_{i}-w_{0})^5$

1. Calculate the gradient with respect to the parameters $w_{1}$ and $w_{0}$. 
   
   Let $u=y_{i}-w_{1}x_{i}-w_{0}$. $Loss=\frac{1}{m}\sum^{m}_{i=1}u^{5}$, $\frac{\delta}{\delta u}=5u^{4}$, $\frac{\delta u}{dw_{0}}=$