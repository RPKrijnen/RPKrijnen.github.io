# Bayesian inference

Bayesian inference is hard...

We can try to find analytical solutions though by exploiting conjugacy between prior and likelihood distributions.
Another option is to use sampling methods like Markov Chain Monte Carlo (MCMC) in order to sample from the posterior.
The final option is to minimize the difference between some easier distribution and the posterior and work with the former to argue about the latter.
This last approach is computationally faster than MCMC, but is ofcourse not guaranteed to be close to the true posterior.