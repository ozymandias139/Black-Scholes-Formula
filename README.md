# Black-Scholes-Formula
The derivation and python realization of Black-Scholes Formula

### Derivation of the Black-Scholes Formula

Given the spot price $S(T)$ at time $T$ :
$S(T) = S_0 \cdot e^{\left( r - \frac{\sigma^2}{2} \right)T + \sigma \sqrt{T} Z}$

where $Z \sim N(0,1)$ is a standard normal variable.

We need to derive the following expectation:

$e^{-rT} \mathbb{E}[\max(S(T) - K, 0)]$

This represents the price of a European call option. To find this, we follow these steps:

1.**Find the distribution of $S(T)$ :**

The given formula can be rewritten as:
$S(T) = S_0 \cdot e^{X}$

where: $X = \left( r - \frac{\sigma^2}{2} \right)T + \sigma \sqrt{T} Z$

Since
$Z \sim N(0,1)$, 
$X \sim N\left( \left( r - \frac{\sigma^2}{2} \right)T, \sigma^2 T \right)$.

Therefore, $S(T)$ follows a log-normal distribution.

2.**Compute the expectation:**

We need to compute $\mathbb{E}[\max(S(T) - K, 0)]$:

$$
\mathbb{E}[\max(S(T) - K, 0)] = \mathbb{E}[(S(T) - K) \cdot \mathbf{1}_{\{S(T) > K\}}]
$$

Using risk-neutral valuation and the properties of the log-normal distribution, the expectation can be found as:

$$
\mathbb{E}[(S(T) - K) \cdot \mathbf{1}_{\{S(T) > K\}}] = S_0 \Phi(d_1) - K e^{-rT} \Phi(d_2)
$$

 where

$$
d_1 = \frac{\ln\left(\frac{S_0}{K}\right) + \left(r + \frac{\sigma^2}{2}\right)T}{\sigma \sqrt{T}}, \quad d_2 = d_1 - \sigma \sqrt{T}
$$

Therefore, the price of the European call option is:

$$
e^{-rT} \mathbb{E}[\max(S(T) - K, 0)] = S_0 \Phi(d_1) - K e^{-rT} \Phi(d_2)
$$

This is the famous Black-Scholes formula for the price of a European call option.

### Plotting the Distribution of $S(T)$ and $log(S(T))$

See in file 'Distribution'

The distributions of $S(T)$ and $log(S(T))$ are shown below:


![Distribution Image](https://github.com/ozymandias139/Black-Scholes-Formula/assets/129940989/57e8f3a2-2267-4c65-9535-1852550ba686)

It can be seen that both distributions are roughly normal.

### Implementing the Formula in Python

See in file 'Implementing the Formula'
![image](https://github.com/ozymandias139/Black-Scholes-Formula/assets/129940989/e19a489a-00d6-4803-8bac-aa65009e92a9)





