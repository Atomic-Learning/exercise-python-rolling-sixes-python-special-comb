Write a function which calculates the probability of $k$ successes being rolled for given values of the probability of success $p$, total number of trials $n$, and $k$. As a reminder, the equation for the binomial probability is:

$$
P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}
$$

where $\binom{n}{k}$ is the binomial coefficient. Use `scipy.special.comb`{.python} to calculate the binomial coefficient.

```py-cell
# Import the functions and packages you need.

# Define a function for the binomial probability.
def binomial_probability(p, n, k):
```

A fair six-sided die is rolled 100 times. Treat rolling a six as a success, so the probability of success on each roll is $p=\frac{1}{6}$.

In the cell above, call your function to calculate the probability of rolling exactly 16 sixes in 100 rolls. You should get an answer around 0.106.

Click below to reveal the solution:

> [!HIDDEN]
> ```py-cell
> from scipy.special import comb
>
> def binomial_probability(p, n, k):
>     return comb(n, k) * p**k * (1-p)**(n-k)
>
> # Example usage:
> probability_16_sixes = binomial_probability(1/6, 100, 16)
> print(probability_16_sixes)
> ```

## Add probabilities

Use your function to calculate the probability of rolling 10 or fewer sixes. You should get an answer around 0.043. Click below for hints:

>[!HIDDEN]
> You can do this by adding the probabilities for $k=0,1,\ldots,10$.
> You may be able to apply your function to an array of values for $k$ and then sum the results.

```py-cell
# Calculate the probability of 10 or fewer sixes.
```

Click below to see a sample solution:
> [!HIDDEN]
> In this sample solution we create a NumPy array of values for $k$ from 0 to 10 and then pass this array to the `binomial_probability` function, which returns an array calculating the probabilities for each value of $k$. We then sum these probabilities to get the total probability of rolling 10 or fewer sixes.
>
> ```py-cell
> import numpy as np
>
> k_values = np.arange(0, 11)
> probability = sum(binomial_probability(1/6, 100, k_values))
> print(probability)
> ```