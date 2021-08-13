---
layout: post
title:  "Statistics Notes"
date:   2021-01-20
category: statistics
---
### 1. Bayesian Inference

1. Assign prior probabilities to parameters
1. Observe data
1. Update probabilities via Bayes' rule 

#### Bayes' rule

$$\newcommand{\P}{\textbf{P}}
\newcommand{\T}{\Theta}
\newcommand{\t}{\theta}
\newcommand{\S}{\mathcal{S}}
\newcommand{\A}{\mathcal{A}}
\newcommand{\R}{\mathcal{R}}
\newcommand{\E}{\textbf{E}}
\newcommand{\deq}{\dot{=}}
\newcommand{\argmax}[1]{\text{argmax}_{#1} \text{ }}
\newcommand{\eps}{\varepsilon}
\newcommand{\N}{\text{Normal}}
\newcommand{\Exp}{\text{Exponential}}
\newcommand{\Erlang}{\text{Erlang}}
\newcommand{\Indicator}{\text{Indicator}}
\newcommand{\Var}{\textbf{Var}}
\newcommand{\Xbar}{\overline{X}}
\newcommand{\xbar}{\overline{x}}
\newcommand{\Ybar}{\overline{Y}}
f_{\Theta\mid X}(\theta \mid x)=\frac{f_{X \mid \Theta}(x \mid \theta) f_\Theta(\theta)}{f_X(x)}$$

#### Bayes' rule for independent samples

$$\begin{align}f_{\Theta\mid X_1...X_n}(\theta\mid x_1,...,x_n) &\propto f_{X_1...X_n\mid \Theta}(x_1,...,x_n\mid \theta)f_{\Theta}(\theta)\\
&=f_{X_1\mid \Theta}(x_1\mid \theta)...f_{X_n\mid\Theta}(x_n\mid \theta)f_{\Theta}(\theta)
\end{align}$$

#### The Erlang($k, \lambda$) random variable

* model: $X_1, ..., X_n$ are independent Exponential($\T$)

* prior: $\T$ is Exponential($x_0$)

* posterior: $\T \mid X_1...X_n$ is Erlang($n+1$, $x_0+X_1+...+X_n$)

$$f(\theta)=\frac{\lambda^k \theta^{k-1} e^{-\lambda \theta}}{(k-1)!}$$

$$\text{where } k=n+1, \lambda = x_0+x_1+...+x_n$$

#### Inference for Normals

* $X_i$= Normal$(\T, \sigma_i)$ independent given $\T$

* $\T$ is Normal$(x_0,\sigma_0)$

* $(\T \mid X_1=x_1,...,X_n=x_n)$ is Normal$(x,\sigma)$ where

$$1/\sigma^2 = 1/\sigma^2_0+...+1/\sigma^2_n$$

$$x/\sigma^2 = x_0/\sigma_0^2 + ... + x_n/\sigma_n^2$$

When $\sigma_0=...=\sigma_n=1$: 

$$(\T \mid X_1=x_1,...,X_n=x_n) \text{ is } Normal \left (\frac{x_0+...+x_n}{n+1},\frac{1}{\sqrt{n+1}} \right) $$

#### Beta($\alpha,\beta$) random variable

* Beta$(1,1)$=Uniform$(0,1)$

* $\T$ is  Beta$(1,1)$

* For $\text{Binomial}(n, \T)$, $(\T \mid h \text{ heads}, t \text{ tails})$ is Beta$(h+1, t+1)$

$$f(\t)=\frac{1}{B(\alpha, \beta)} \t^{\alpha-1} (1-\t)^{\beta-1} \text{ when } 0<\t<1$$

$$\text{where } B(\alpha, \beta) = (\alpha-1)! (\beta-1)! /(\alpha+\beta-1)!$$

<br>
<hr>
<br>

### 2. Bayesian Estimation and Hypothesis Testing
#### Point Estimation

* Conditional expectation estimator:

$$\E[\T\mid X=x]$$

* Maximum *a posteriori* (MAP) estimator

$$\argmax{\t} f_{\T\mid X}(\t\mid x)$$

#### Point estimation for normals

$X_i$= $\N(\T,1)$ independent given $\T$

$(\T\mid X_1=x_1,...,X_n=x_N)$ is $\N(x=\frac{x_0+...+x_n}{n+1}, 1/\sqrt{n+1})$

CE estimate: $\E[\N(x, \frac{1}{\sqrt{n+1}})]=x$

MAP estimate: $x$

#### Point estimation for Beta

CE estimate: $\frac{\alpha}{\alpha+\beta}=\frac{h+1}{h+t+2}$

MAP estimate: $\frac{h}{h+t}$

#### Hypothesis testing

Suppose $\T$ takes two values

$$\text{MAP}=\argmax{\t} f_{\T\mid X}(\t\mid x)$$

Compare $f_{\T \mid X}(1\mid x)\propto f_{X\mid\T}(x\mid 1)f_\T(1)$ to $f_{\T \mid X}(0\mid x)\propto f_{X\mid\T}(x\mid 0)f_\T(0)$

For Beta random variable,

$$\text{CE}=\alpha / (\alpha+\beta)$$

$$\text{MAP}=h/(h+t)$$

#### Binary hypothesis testing error

$$\begin{align}
\textbf{error} &= \P(\hat{\T}\neq \T )
\end{align}$$

#### MAP hypothesis testing error 

$\T$ takes $k$ possible values

$$\P(MAP \neq \T)\leq 1-\frac{1}{k}$$

<br>
<hr>
<br>

### 3. Sample Statistics

#### Random sample

A random sample is a joint outcome of $n$ independent random variables $X_1, ..., X_n$ with same PDF/PMF.

#### Sample mean

The sample mean is the random variable

$$\Xbar = \frac{X_1+...+X_n}{n}$$

The sample mean is an estimator of the actual mean $\mu$.

$$\P(\mid \Xbar - \mu \mid \geq \eps) \leq \delta$$

where $\eps$ is the sampling error and $\delta$ is the confidence error.

#### Properties of sample mean

Unbiased: For every $n$

$$\E[\Xbar]=\mu$$

Consistent: For every $\eps$, $\delta$ and sufficiently large $n$

$$\P(\mid \Xbar - \mu\mid\geq \eps)\leq \delta$$

$$n\geq \frac{\sigma^2}{\eps^2 \delta}$$

(CLT) Asymptotically normal deviation: For every $t$

$$\lim_{n\rightarrow \infty} \P(\Xbar \leq \mu + t\sigma/\sqrt{n}) = \P(\N(0,1)\leq t)$$

where $\mu=\E[\Xbar]$ and $\sigma/ \sqrt{n}=\sqrt{\Var [\Xbar]}$,

where $\sigma$ is the standard deviation of the distribution.

#### Sample variance

$$\begin{align}
V=\Var[Samp]&=\E[(Samp-\Xbar)^2]\\
&=\frac{(X_1-\Xbar)^2+...+(X_n-\Xbar)^2}{n}\\
&=\frac{X_1^2+...+X_n^2}{n}-\left[\frac{X_1+...+X_n}{n}\right]^2\\
\end{align}$$

Expectation of the sample variance in terms of actual variance

$$\E[V]=\frac{n-1}{n}\sigma^2$$

#### Unbiased estimator of actual variance $\sigma^2$

$$S^2=\frac{n}{n-1}\Var(Samp)=\frac{(X_1-\Xbar)^2+...+(X_n-\Xbar)^2}{n-1}$$

<br>
<hr>
<br>

### 4. Point Estimation

#### Estimator for $\t$, $\hat{\T}_n$

$X = (X_1, ..., X_n)$ independent samples

Unbiased estimator:

$$\E[\hat{\T}_n]=\t , \forall n$$

Consistent estimator:

$$\hat{\T}_n \text{ converges to }\theta \text{ in probability}$$

$$\P(\mid \hat{\T}_n - \T \mid \geq \eps) \leq \delta, \forall \eps, \delta \text{ if } n \text{ is sufficiently large.}$$

#### Minimum variance principle
Among unbiased estimators, it is preferable to choose the one with smaller variance.

#### Maximum likelihood

$$\textbf{maximize } f_X(x\mid \theta)$$

ML = MAP without a prior

#### Maximum likelihood for Indicator($\t$)

$k$ heads, $n-k$ tails.

$$ MLE = \frac{k}{n} \text{ (Unbiased)}$$

#### Maximum likelihood for Exponential($\lambda$)

$n$ samples at times $T_1, T_1+T_2,...,T_1+...+T_n$

$$ MLE = \frac{n}{T_1+...+T_n} \text{ (Biased but consistent)}$$

#### Maximum likelihood for Normal($\mu, \sigma$)

$(X_1, ..., X_n)$ independent Normal($\mu, \sigma$)

$$MLE \text{ of } \mu: \Xbar = \frac{X_1+...+X_n}{n} \text{ (Unbiased, with smallest variance)}$$

If $\mu$ is known,

$$MLE \text{ of } \sigma^2 = \frac{(X_1-\mu)^2+...+(X_n-\mu)^2}{n}$$

<br>
<hr>
<br>

### 5. Confidence

#### Confidence intervals

A $p$-confidence interval is a pair $$\hat{\T}_-, \hat{\T}_+$$ (width) so that 

$$\P(\theta \text{ is between } \hat{\T}_{-}\text{ and } \hat{\T}_{+}) \geq p$$

#### Confidence interval for normal mean

$X_1, X_2, ..., X_n$ are $\N(\mu , \sigma)$ samples. Sample mean $\Xbar$ is $\N(\mu, \sigma/\sqrt{n})$.

$$\P(\Xbar - z_-\sigma/\sqrt{n}\leq \mu \leq \Xbar + z_+\sigma/\sqrt{n})=\P(-z_+ \leq \N(0,1) \leq z_-)$$

$95\%$ confidence for $z_- = z_+ \approx 1.96$.

#### Confidence interval for exponential mean

$X_1,X_2,...,X_n$ are $\Exp(\lambda)$ samples. $n\lambda\Xbar$ is $\Erlang(n,1)$.

$$\P(n\Xbar/z_+ \leq 1/\lambda \leq n\Xbar/z_-)=\P(z_-\leq \Erlang(n,1)\leq z_+)$$

#### Confidence interval for $\Indicator(p)$

$$\P(A-Bz\leq p\leq A+Bz)\approx \P(-z\leq \N(0,1)\leq z)$$

$$A=\frac{\Xbar+z^2/2n}{1+z^2/n}, B=\frac{\sqrt{\Xbar(1-\Xbar)/n + z^2/4n^2}}{1+z^2/n}$$

Simplified confidence interval

$$A=\Xbar$$

$$B=\sqrt{\frac{\Xbar(1-\Xbar)}{n}}$$

#### Confidence bound

A $p$-upper confidence bound is $\T$ so that

$$\P(\t\leq \T)\geq p$$

A $p$-lower confidence bound is $\T$ so that 

$$\P(\t\geq\T)\geq p$$

#### Confidence bound for normal mean

$\Xbar$ is mean of $n$ $\N(\mu,\sigma)$ samples

$$\P(\mu\leq\Xbar+z\sigma/\sqrt{n})=\P(\N(0,1)\geq -z)$$

$$\P(\mu \geq \Xbar-z\sigma/\sqrt{n})=\P(\N(0,1)\leq z)$$

<br>
<hr>
<br>

### 6. Confidence for Normals

#### Normal algebra review

$$\N(\mu, \sigma)=\mu+\sigma\N(0,1)$$

$X_1=\N(\mu_1, \sigma_1), X_2=\N(\mu_2, \sigma_2)$,

$$aX_1+bX_2 = \N(a\mu_1+b\mu_2, \sqrt{a^2\sigma_1^2+b^2\sigma_2^2})$$

#### The $\chi^2(k)$ random variable

$$X^2=N_1^2+...+N_k^2=\chi^2(k)$$

$$f(x)\propto x^{k/2-1}e^{-x/2}$$

#### Confidence intervals of $\sigma$ for $\N(\mu, \sigma)$

$$(n-1) S^2/\sigma^2 = \chi^2(n-1)$$ 

$$\begin{align}
\P(z_-\leq \chi^2(n-1)\leq z_+)&=\P(z_-\leq \frac{(n-1)S^2}{\sigma^2}\leq z_+)\\
&=\P\left(\sqrt{(n-1)S^2/z_+}\leq \sigma\leq \sqrt{(n-1)S^2/z_-}\right)
\end{align}$$

#### The $t(k)$ student random variable

$$T=\frac{\Xbar-\mu}{S/\sqrt{n}}$$

$$t(k)=\frac{\N(0,1)}{\sqrt{\chi^2(k)/k}}$$ 

$$\rightarrow \N(0,1) \text{ as } k\rightarrow \infty$$

#### Confidence intervals of $\mu$ for $\N(\mu, \sigma)$

$$\begin{align}
\P(\Xbar-z_+\frac{S}{\sqrt{n}}\leq\mu\leq \Xbar-z_-\frac{S}{\sqrt{n}})&=\P(z_-\leq \frac{\Xbar-\mu}{S/\sqrt{n}}\leq z_+)\\
&=\P(z_-\leq t(n-1)\leq z_+)
\end{align}$$

For $95\%$ confidence interval, $-z_-=z_+=2.776$.

#### Confidence for normals

Estimate $\mu$ with known $\sigma$ | $\frac{\Xbar-\mu}{\sigma/\sqrt{n}}$ is $\N(0,1)$
Estimate $\sigma$ | $\frac{(n-1)S^2}{\sigma^2}$ is $\chi^2(n-1)$
Estimate $\mu$ with unknown $\sigma$ | $\frac{\Xbar-\mu}{S/\sqrt{n}}$ is $t(n-1)$

#### Prediction intervals for $\N(\mu, \sigma)$

$$\frac{\Xbar-X_{n+1}}{S\sqrt{1+1/n}} \text{ is } t(n-1)$$

$$\P(\Xbar-z_+S\sqrt{1+1/n}\leq X_{n+1} \leq \Xbar-z_- S \sqrt{1+1/n})=\P(z_-\leq t(n-1)\leq z_+)$$

<br>
<hr>
<br>

### 7. Hypethesis Testing

#### Hypothesis testing terminology

Hypothesis: PDF/PMF of a random variable

* Null $H_0$: Default PMF/PDF
* Alternative $H_1$: Conjectured PMF/PDF

Test: (function) outcome $$\rightarrow \{+,-\}$$

False positive (type I error): $P_{H_0}(\text{test}=+)$

False negative (type II error): $P_{H_1}(\text{test}=-)$

#### Neyman-Pearson Lemma

Among all tests with given false negative probability, the false positive is minimized by the one that picks samples with largest likelihood ratio.

$$\frac{f_{X_1}(x)}{f_{X_0}(x)}$$

#### $p$-value

The $p$-value is the smallest value of the type I error that would have caused the test to reject the null hypothesis for a given outcome. 

Smallest __False Positive__ that would accept $H_1$ (rejects $H_0$) for a given outcome.

(Small $p$-value means confident that alternative holds, and vice versa.)

![]({{ '/assets/images/unlisted/statistics-notes/p-value.png' | relative_url }}){: style="width: 80%;" class="center"}

<br>
<hr>
<br>

### 8. Comparing Populations

#### Comparing normal means (Known variance)

Assume independence,

$$X_1,...,X_m \sim \N(\mu_1, \sigma_1)$$

$$Y_1,...,Y_n \sim \N(\mu_2, \sigma_2)$$

$H_0$: $\mu_1=\mu_2$

$$\begin{align}
\Xbar - \Ybar &= \N(\mu_1, \frac{\sigma_1}{\sqrt{m}}) - \N(\mu_2, \frac{\sigma_2}{\sqrt{n}})\\
&=\N(\mu_1-\mu_2, \sqrt{\frac{\sigma_1^2}{m}+\frac{\sigma_2^2}{n}})
\end{align}$$

p-value $= \N(0, \sqrt{\frac{\sigma_1^2}{m}+\frac{\sigma_2^2}{n}}) > \Xbar - \Ybar)$

#### Comparing normal means (Unknown variance)

Assume independence,

$$X_1,...,X_m \sim \N(\mu_1, \sigma)$$

$$Y_1,...,Y_n \sim \N(\mu_2, \sigma)$$

$$T=\frac{\Xbar-\Ybar}{\sqrt{\frac{1}{m}+\frac{1}{n}}\sqrt{\frac{m-1}{m+n-2}S_X^2+\frac{n-1}{m+n-2}S_Y^2}} \text{ is } t(m+n-2)$$

<!-- T\ =\ \frac{\left(X-Y\right)}{\sqrt{\frac{1}{m}+\frac{1}{n}}\sqrt{\frac{\left(m-1\right)}{m+n-2}S_{x}^{2}+\frac{\left(n-1\right)}{m+n-2}S_{y}^{2}}}-->

#### Paired t-test

$$Z_1,..., Z_n \text{ independent } \N(\mu, \sigma)$$

where $Z_i=X_i-Y_i$

$H_0$: $\mu=0$

Test for Normal with unknown $\sigma$

$$\frac{\overline{Z}}{S_{\overline{Z}}/\sqrt{n}} \text{ is a } t(n-1) \text{ random variable.}$$

#### Comparing population proportions

$X_1,...,X_m$ independent Indicator($p_1$)

$Y_1,...,Y_n$ independent Indicator($p_2$)

$$\E[\Xbar-\Ybar] = \E[\Xbar] - \E[\Ybar] = p_1 - p_2$$

$$\Var[\Xbar-\Ybar]=\Var[\Xbar]+\Var[\Ybar]=\frac{p_1(1-p_1)}{m}+\frac{p_2(1-p_2)}{n}$$

Null hypothesis: $p_1=p_2$

$$\Xbar-\Ybar \approx \N \left (0, \sqrt{p(1-p)}\sqrt{\frac{1}{m}+\frac{1}{n}} \right)$$

$$\Rightarrow \frac{\Xbar-\Ybar}{\sqrt{\hat{p}(1-\hat{p})}\sqrt{\frac{1}{m}+\frac{1}{n}}}=\N(0,1) \text{ as } m, n \rightarrow \infty \text{ where } \hat{p}=\frac{X+Y}{m+n}$$

Reasonable if $m\hat{p_1}, m(1-\hat{p_1}), n\hat{p_2}, n(1-\hat{p_2}) \geq 10$

#### Comparing normal variances

$X_1,...,X_n$ independent $\N(\mu_1, \sigma_1)$

$Y_1,...,Y_n$ independent $\N(\mu_2, \sigma_2)$

Null hypothesis: $\sigma_1=\sigma_2$

$$\frac{S_1^2}{S_2^2}=\frac{\sigma_1^2}{\sigma_2^2}F(m-1,n-1)$$

where $F(m-1,n-1)=\frac{\chi^2(m-1)/(m-1)}{\chi^2(n-1)/(n-1)}$

### 9. Goodness of fit

#### The chi-square test for uniformity

$$X^2=\frac{(N_1-n/k)^2}{n/k}+...\frac{(N_k-n/k)^2}{n/k}$$

If $n \rightarrow \infty$, $X^2 = \chi^2(k-1)$

p-value = $\P(\chi^2(k-1)\geq X^2)$ assuming $n/k \geq 5$.

* Large $\chi^2$/small p-value $\Rightarrow$ confident in alternative hypothesis
* Small $\chi^2$/large p-value $\not\Rightarrow$ confident in null hypothesis

#### The general chi-square test
$p_1,...,p_k$ hypothesized frequencies

$N_1,..., N_k$ empirical counts

$$X^2=\frac{(N_1-np_1)^2}{np_1}+...+\frac{(N_k-np_k)^2}{np_k}$$

As $n\rightarrow \infty$, $X^2\rightarrow \chi^2(k-1)$

p-value = $\P(\chi^2(k-1)\geq X^2)$

#### Chi-square test for continuous random variables
Null hypothesis: pdf $f(x)$

1. Divide range into $k$ buckets $B_1,...,B_k$ such that $\P(X\in B_1)=...=\P(X\in B_k)=1/k$
2. Sort data into buckets
3. Perform $\chi^2$ test for fair $k$-sided die

($n/k$ should be $\geq 5$)

#### Fisher's Theorem
$N_1,...,N_k$ empirical counts

$p_1(\t),...,p_k(\t)$ hypothesized frequencies

$\hat{P}_1,..., \hat{P}_k$ maximum likelihood estimates

$$X^2=\frac{(N_1-n\hat{P}_1)^2}{n\hat{P}_1}+...+\frac{(N_k-n\hat{P}_k)^2}{n\hat{P}_k}$$

$$X^2 \rightarrow \chi^2(k-2) \text{ as } n\rightarrow \infty$$

#### Fisher's Theorem with multiple parameters

$p_1(\t),...,p_k(\t)$ hypothesized frequencies

$\t=(\t_1,...,\t_s)$

$$X^2=\frac{(N_1-n\hat{P}_1)^2}{n\hat{P}_1}+...+\frac{(N_k-n\hat{P}_k)^2}{n\hat{P}_k}$$

$$X^2 \rightarrow \chi^2(k-1-s) \text{ as } n\rightarrow \infty$$

#### Chi-square test for independence

Null hypothesis: Row and column features are independent

$$\hat{P}_i=\frac{N_{i1}+...+N_{ic}}{n}$$

$$\hat{Q}_j=\frac{N_{1j}+...+N_{rj}}{n}$$

$$d.f. = (r-1)(c-1)$$

$$X^2=\sum_{ij}\frac{(N_{ij}-n\hat{P}_i\hat{Q}_j)^2}{n\hat{P}_i\hat{Q}_j} \text{ is } \chi^2(d.f.) \text{ as } n\rightarrow \infty$$

#### Charnoff-Lehmann theorem

1. Estimate $s$ parameters
2. Set up $k$ equiprobable buckets
3. $N_i=$ samples in bucket $i$

$$X^2=\frac{N_1-n/k}{n/k}+...+\frac{N_k-n/k}{n/k}$$

$$\chi^2(k-1-s)\leq X^2\leq \chi^2(k-1) \text{ as } n\rightarrow \infty$$

### 10. Modelling Dependence

#### Regression coefficients

$$Y_i=\beta_0+\beta_1 x_i + N_i$$

Choose $\beta_0,\beta_1$ that minimize $N_1^2+...+N_n^2$.

$$\hat{\beta}_1= \frac{\sum_{i=1}^{n} (X_i-\Xbar)(Y_i-\Ybar)}{\sum(X_i-\Xbar)^2}$$

$$\hat{\beta}_0=\Ybar - \hat{\beta}_1 \Xbar$$

where $\Xbar = \frac{X_1+...+X_n}{n}$ and $\Ybar = \frac{Y_1+...+Y_n}{n}$.

#### Coefficient of determination

$$1-\frac{\Var[N]}{\Var[Y]} \text{ is estimated by } r^2=1-\frac{\sum(Y_i-\hat{\beta}_0-\hat{\beta}_1 x_i)^2}{\sum(Y_i-\Ybar)^2}$$

Always between 0 and 1.

#### Regression to the mean

If $X,Y$ have same marginals,

$$\E[Y\mid X\geq x] \leq \E[X\mid X\geq x]$$

$$\E[Y\mid X\leq x]\geq \E[X\mid X\leq x]$$


