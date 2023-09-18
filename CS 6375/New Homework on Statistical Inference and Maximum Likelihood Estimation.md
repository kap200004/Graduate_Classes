# New Homework on Statistical Inference and Maximum Likelihood Estimation

## Question 1

As a reliability engineer at a factory that produces LEDs, you are tasked with estimating the failure rate of the LEDs. You conduct a series of tests in which several LEDs are used until one fails. The number of trials before failure, $n$, is recorded.

- Given that$q$is the failure probability, what is the probability of$n$trials before a failed LED is found?
- You perform$t$independent tests and record $n_1, n_2, \ldots, n_t$. Provide the most likely value for $q$ based on the recorded data.

## Question 2

Let $\alpha$be the probability that a die shows an even number and $2\alpha$ be the probability that it shows a prime number. You roll the die 8 times and observe the following outcomes:

|Even|Odd|Even|Prime|Odd|Prime|Odd|Prime|
|---|---|---|---|---|---|---|---|

- What is the likelihood of the data given $\alpha$?
- Compute the maximum likelihood estimate of $\alpha$.

## Question 3

Write down the log-likelihood for the data and derive the expression for the maximum likelihood estimates for the following distributions:

- Poisson distribution defined by$\lambda$; find the MLE for $\lambda$.
- Exponential distribution defined by $\beta$; find the MLE for $\beta$.

## Question 4

You have a pair of dice and a spinner. You put Beta priors $\beta(3, 7)$ and $\beta(10, 10)$ on the dice and the spinner respectively. You roll the dice and spin the spinner 50 times. You get 10 'sixes' from the dice and 20 successful spins. Answer the following:

- Is the MLE estimate for both the dice and the spinner the same?
- Is the MAP estimate for the dice greater than the MAP estimate for the spinner?

## Question 5

You have a biased coin with $p$ being the probability of landing heads. You flip the coin 10 times and get 4 heads and 6 tails. Suppose $p$ can only be 0.2 or 0.7. Find the Maximum Likelihood Estimate of $p$ from the given set ${0.2, 0.7}$.

## Question 6

Suppose you have a prior on$p$such that$P(p=0.2)= 0.3$ and $P(p=0.7)= 0.7$. Given the same coin flip data as in Question 5, find the MAP estimate of $p$ from the set ${0.2, 0.7}$ using this prior.