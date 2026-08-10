---
title: "Abstractions and their Meaning I: A Primer on Probability and Information Theory"
excerpt: ""
last_modified_at: 2026-08-10T20:00:00-00:00
author_profile: false
# header:
#  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories: [information theory]
toc: true
---


<!-- --- -->
## Probability Theory

### Fundamental axioms
- Axioms: non-negativity, unity, and additivity

- Basic theorems:
    - Probability is bounded: $p(x) \in [0,1]$
    - Total probability is conserved: $\int p(x) dx = 1$

### The Expectation Operator
<!-- meaning of E -->
$\mathbb{E}_{x \sim p(x)}[f(x)] := \int p(x) f(x) dx$

### Orthogonality vs. independence 
- Independence: $p(x,y) = p(x)p(y)$
- Orthogonality: $\mathbb{E}_{x,y}(xy) = 0$
- Independence is stronger than orthogonality: A pair of RVs can be orthogonal but still be statistically dependent (e.g. via non-linear relationship)

### PDFs of composite RVs
- $p_z(z = x + y) = conv(p_x(x), p_y(y))$
- $p_z(z = xy) = \int \frac{1}{|x|} p_x(x) p_y(\frac{z}{x}) dx = \int \frac{1}{|y|} p_y(y) p_x(\frac{z}{y})$ (where x and y are independent RVs)

### Selected Theorems
- Jensen's inequality: $E(f(x)) \geq f(E(x))$
- Tweedie's formula
    - Let $x = u + e$, where $x$ is observed noisy variable, $u$ is clean latent variable, and $e$ is Gaussian noise
    - Then, $\hat{x}_\text{mmse} = \mathbb{E}[u | x] = \int u p(u|x) du$
    - Tweedie's analytical formula: $\hat{x}_\text{mmse} = x + \sigma^2 \frac{\nabla p(x)}{p(x)}$
        - Where the first term is the max-likelihood and the second term is the Bayes correction


<!-- --- -->
## Information Theory

### Entropy measures
- Entropy: $H(x) = \mathbb{E}_x[ -log p(x) ]$
- Conditional entropy: $H(x|y) = \mathbb{E}_{x,y}[ -log p(x|y) ] = \mathbb{E}_{x,y}[ -log \frac{p(x,y)}{p(y)} ]$
    - Asymmetric: $H(x|y) \neq H(y|x)$
- Joint entropy: $H(x,y) = \mathbb{E}_{x,y}[ -log p(x,y) ]$
- Cross entropy: $H_x(y) = \mathbb{E}_{x}[ -log p(y) ]$
    - Asymmetric: $H_x(y) \neq H_y(x)$
- Mutual information: $I(x;y) = \mathbb{E}_{x,y}[ -log \frac{p(x,y)}{p(x)p(y)} ]$
    - Symmetric: $I(x;y) = I(y;x)$
- KL divergence: $D_{KL}(p||q) = E_{x \sim p(x)}[ log \frac{p(x)}{q(x)} ]$
    - Asymmetric: $D_{KL}(p||q) \neq D_{KL}(q||p)$
    - Unbounded: $[0, \infty)$
        - $D_{KL}(p||q)=0$ if and only if p and q are identical
        - If $support(p) \not\subseteq support(q)$, then $D_{KL}(p||q) = \infty$; if $support(p) \subseteq support(q)$ then $D_{KL}(p||q)$ may more may not be $\infty$.

- JS divergence: $JSD(p||q) = \frac{1}{2}D_{KL}(p||m) + \frac{1}{2}D_{KL}(q||m)$
    - where $m = \frac{1}{2} (p+q)$ is the mean distrib
    - $JSD(p||q) = H(\frac{p+q}{2}) + \frac{H(p)+H(q)}{2}$
    - Symmetric: $JSD(p||q) = JSD(q||p)$
    - Bounded in [0,1] when using base-2
    - $\sqrt{JSD}$ is a true metric distance (satisfies triangle inequality)


### Relationship between entropy measures
(Information diagram is a useful tool)
- $H(x,y) = H(x) + H(y) - I(x;y)$
    - If a and y are independent: $I(x;y)=0 \implies H(x,y) = H(x) + H(y)$
- $H(x) = H(x|y) + I(x;y)$
- $I(x,y) = D_{KL}(p(x,y) || p(x)p(y))$

- Relationship between entropy and variance:
    - Var measures the average distance of the RV from its mean; defined only for numerical RVs
    - entropy measures concentration of the probability mass; more fundamental and general


### Entropy measures of known distributions
- Entropy of the Gaussian distribution:


### Entropy of composite RVs
- $H(x+y)$: non-trivial, but bounded
    - Lowerbound: $H(x+y) \geq \max(H(x), H(y))$
    - Upperbound: $H(x+y) \leq H(x,y) = H(x) + H(y)$
- $H(xy)$: non-trivial


### Other notions of information
- Fisher information:
    - "The Fisher information is a way of measuring the amount of information that an observable random variable $X$ carries about an unknown parameter $\theta$ upon which the probability of $X$ depends." (wikipedia)
    - $\mathcal{I}(\theta) = \mathbb{E}[ (\frac{\partial}{\partial \theta} log f(X;\theta))^2 \mid \theta ]$


### Theorems (with symbolic + graphical proofs)
- Gibbs' inequality: $E_{x\sim p(x)}[ -log p(x) ] \leq E_{x\sim p(x)}[ -log q(x) ]$
- Laplace's Principle of Insufficient Reason (aka Principle of Indifference): If there are \(n\) possible outcomes for an event and no evidence suggests one is more likely than another, each should be assigned an equal probability of \(1/n\).
- MaxEnt principle: Among all distributions consistent with a given set of constraints, the distribution that maximizes entropy should be selected.



# Resources
- Jaynes - Probability Theory: The Logic of Science
- Sivia, Skilling - Data Analysis: A Bayesian Tutorial
- David MacKay - Information Theory, Inference, and Learning Algorithms
- Polyanskiy, Wu - Information Theory: From Coding to Learning
- Cover - Elements of Information Theory
- Baez - What is Entropy?
- Varley - Syntropy. [(docs)](https://syntropy.readthedocs.io/en/stable/index.html)