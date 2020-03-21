## Simple Linear Regression
- We assume a model
  $$
  Y = \beta_0 + \beta_1X + \epsilon
  $$
  where $\beta_0$ and $\beta_1$ are two unknown constants that represent the _intercept_ and _slope_, also known as coefficients or parameters, and $\epsilon$ is the error term

- Given some estimates $\hat{\beta_0}$ and $\hat{\beta_1}$ for the model, we can predit
  $$
  \hat{y} = \hat{\beta_0} + \hat{\beta_1}x
  $$
  where the _hat_ symbol denotes an estimated value

- Estimation of parameters by least squares
  
  $e_i$ = $y_i$ - $\hat{y_i}$ represents the _i_th residual

  The _residual sum of squares_ (RSS) are deinfed as
  $$
  RSS = e_1^2 + e_2^2 + ... + e_n^2
  $$

  The least squares approach chooses $\hat{\beta_0}$ and $\hat{\beta_1}$ to minimise the RSS. The minimising values can be shown to be 
  $$
  \hat{\beta_1} = \frac{\sum(x_i - \bar{x})(y_i - \bar{y})}{\sum(x_i - \bar{x})^2}
  $$

  $$
  \hat{\beta_0} = \bar{y} - \hat{\beta_1}\bar{x}
  $$

- The standard erros of an estimator reflects how it  varies under repeated sampling. We have
  $$
  SE(\hat{\beta_1})^2 =  \frac{\sigma^2}{\sum(x_i - \bar{x})^2}
  $$

  $$
    SE(\hat{\beta_0})^2 = \sigma^2\Big[\frac{1}{n} +  \frac{\bar{x}^2}{\sum(x_i - \bar{x})^2}\Big]
  $$
  where $\sigma^2$ = $Var(\epsilon$).
  
  The formula tell us that the more  spread out x is, the more precise we can get

- 95% Confidence intervals for $\hat{\beta_1}$
  $$
    \hat{\beta_1} \pm 2 * SE(\hat{\beta_1})
  $$
  which means there's 95% chance that the interval will contain the true value of $\beta_1$ (under a scenario where we got repeated samples like the present sample)

## Hypothesis Testing and Confidence Intervals
- To test the null hypothesis, we compute a *t-statistics*, given by
  $$
  t = \frac{\hat{\beta_1} - 0}{SE(\hat{\beta_1})}
  $$
- This will have a *t-distribution* with *n - 2* degrees of freedom, assuming $\beta_1 = 0$ 
### Assessing the overall accuracy of the model
- We compute the *Residual Standard Error* (RSS)
  $$
  RSE = \sqrt{\frac{1}{n-2}RSS} = \sqrt{\frac{1}{n-2}\sum(y_i - \hat{y_i})^2},
  $$
  where the *residual sum-of-squares* is RSS = $\sum(y_i - \hat{y_i})^2$
- $R^2$ or fraction of the variance explained is
  $$
  R^2 = \frac{TSS - RSS}{TSS} = 1 - \frac{RSS}{TSS}
  $$
where $TSS = \sum{(y_i - \bar{y})^2}$ is the *total sum of squares*.

## Multiple Linear Regression
- Here our model is
  $$
   Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + ... + \beta_pX_p + \epsilon
  $$
- We interpret $\beta_j$ as the *average* effect on Y of a one unit increase in $X_j$, *holding all other predictors fixed*
- The ideal scenario is when the predictors are uncorrelated. However, in reality, correlations amongst predictors cause problems. The variance of all coefficients tend to increase, sometimes dramatically. Therefore, *claims of causality* should be avoided

## Is at least one predictor useful
- We can use F-statistic
  $$
  F = \frac{(TSS - RSS) / p}{RSS/(n-p-1)} ~ F_{p, n-p-1}
  $$
  where *p* is the number of parameters we fit

- Qualitative predictors take a discrete set of values. They are also called *categorical*predictors or f*actor variables*. For *k* number of qualitative predictors, there'll be *(k-1)* dummy variables created and the one without any dummy variables will be the *baseline*. Note that the statistics can be different from which baseline you choose

## Extensions of the linear model
Removing the additive assumption: *interactions* and *nonlinearity*

### Interactions
- This removes the assumption that each predictor is independent from another
- How to model interactions? We can add another parameter which has the combined effect of other individual parameters and test on if the extra parameter is significant
- Sometimes it is the case that an interaction term has very small p-value, but the associated main effects do not. There's this *hierarchy principle*, saying if we include an interaction in a model, we should also include the main effects, event if the p-values associated with their coefficients are not significant
