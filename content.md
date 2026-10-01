A fair six-sided die is rolled 100 times. Treat rolling a six as a success, so the probability of success on each roll is $p=\frac{1}{6}$.

Write a function which calculates the binomial probability $P(X=k)$ for given values of $p$, $n$, and $k$. Use `scipy.special.comb`{.python} to calculate the binomial coefficient.

```py-cell
# Import the functions and packages you need.

# Define a function for the binomial probability.
def binomial_probability(p, n, k):
```

Use your function to calculate the probability of rolling exactly 16 sixes in 100 rolls.

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

Use your function to calculate the probability of rolling 10 or fewer sixes. You can do this by adding the probabilities for $k=0,1,\ldots,10$.

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