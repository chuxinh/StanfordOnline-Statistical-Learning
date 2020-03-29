## Logistic Regression
- Let $p(X) = Pr(Y = 1|X)$, the logistict regression uses the form:
  $$
  p(X) = \frac{e^{\beta_0 + \beta_1X}}{1 + e^{\beta_0 + \beta_1X}}
  $$
- A big of rearrangement gives the following, which is called the *log odds* or *logit* transformation
  $$
  log(\frac{p(X)}{1-p(X)}) = \beta_0 + \beta_1X
  $$
- We use maximum likelihood to estimate the parameters, which gives the probability of the observed zeros and ones in the data.
  $$
  \ell(\beta_0, \beta) = \prod_{i:y_i=1} p(x_i) \prod_{i:y_i=0} (1-p(x_i))
  $$

## Multivariate Logistic Regression
  $$
  p(X) = \frac{e^{\beta_0 + \beta_1X + ... +\beta_pX_p}}{1 + e^{\beta_0 + \beta_1X_1 + ... +\beta_pX_p}}
  $$

## Discriminant Analysis
- The approach is to model the distribution of $X$ in each of the classes separately, and then use *Bayes theorem* to flip things around and obtain $PR(Y|X)$
- When we use normal (Gaussian) distributions for each class, this leads to linear or quadratic discriminat analysis
- Bayes theorem for classification:
  $$
    PR(Y=k|X=x) = \frac{Pr(X=x|Y=k) * Pr(Y=k)}{Pr(X=x)}
  $$
- One writes this slightly differently for discriminant analysis:
  $$
    Pr(Y=k|X=x) = \frac{\pi_kf_k(x)}{\sum_{l=1}^{K}\pi_lf_l(x)}
  $$
  where $f_k(x) = Pr(X=x|Y=k$ is the *density* for $X$ in class $k$. $\pi_k = Pr(Y=k)$ is the marginal or prior probability for class $k$
- Why discriminant analysis?
  
  1. When the classes are well-separated, the parameter estimates for the logistic regression model are surprisingly unstable. Linear discriminant analysis does not suffer from this problem
  2. If $n$ is small and the distribution of the predictors $X$ is approximately normal in each of   the classes, the linear discriminant model is again more stable than the logistic regression model
  3. Linear discriminant analysis is popular when we have more than two response classes, because it also provides low-dimensional views of the data

### Gaussian Discriminant Analysis - One Variable
- The Gaussian density has the form:
  $$
    f_k(x) = \frac{1}{\sqrt{2\pi\sigma_k}} e^{-\frac{1}{2}(\frac{x-\mu_k}{\sigma_k})^2}
  $$
  where $\mu_k$ is the mean, and $\sigma_k^{2}$ the variance (in class $k$), assuming that all the $\sigma_k = \sigma$ are the same

- To classify at the value $X=x$, we need to see which of the $p_k(x)$ is the largest. Taking logs, and discarding terms that do not depend on $k$, we see that this is equivalent to assigning $x$ to the class with the largest *discriminant score*:
  $$
    \delta_k(x) = x*\frac{\mu_k}{\sigma^2} - \frac{\mu_k^2}{2\sigma^2} + log(\pi_k)
  $$  
  Note that $\delta_k(x)$ is a *linear* function of $x$

### Gaussian Discriminant Analysis - Many Variables
- Density:
  $$
    f(x) = \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} e^{-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)}
  $$
- Discriminant function:
  $$
  \delta_k(x) = x^T\Sigma^{-1}\mu_k - \frac{1}{2}\mu_k^T\Sigma^{-1}\mu_k + log\pi_k
  $$
  