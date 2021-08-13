---
layout: post
title:  "Bayesian Statistics"
date:   2021-01-11
category: statistics
---
<h4>Bayesian inference</h4>

1. Assign prior probabilities to parameters
1. Observe data
1. Update probabilities via Bayes' rule

<h4>Bayes' rule</h4>

$$\newcommand{\T}{\Theta}
\newcommand{\t}{\theta}
f_{\Theta\mid X}(\theta \mid x)=\frac{f_{X \mid \Theta}(x \mid \theta) f_\Theta(\theta)}{f_X(x)}$$

<h4>Bayes' rule for independent samples</h4>

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

When $\sigma_0=...=\sigma_n=1$: Normal($\frac{x_0+...+x_n}{n+1},\frac{1}{\sqrt{n+1}}$)

#### Beta($\alpha,\beta$) random variable

* Beta$(1,1)$=Uniform$(0,1)$

* $\T$ is  Beta$(1,1)$

* $(\T \mid h \text{ heads}, t \text{ tails})$ is Beta$(h+1, t+1)$

$$f(\t)=\frac{1}{B(\alpha, \beta)} \t^{\alpha-1} (1-\t)^{\beta-1} \text{ when } 0<\t<1$$

$$\text{where } B(\alpha, \beta) = (\alpha-1)! (\beta-1)! /(\alpha+\beta-1)!$$

<br>
<hr>
<br>

<h4> Lecture Example 1 ^</h4> 
Romeo is waiting for Juliet on their first date.
Model: 

$$X=\text{Uniform}(0, \Theta)\\ \Theta=\text{Uniform}(0,1)$$

On their first date, Juliet arrives 1/2 hour late.
$$\Rightarrow 1/2 \leq \theta \leq 1$$

$$\begin{align}f_{X \mid \Theta}(\frac{1}{2} \mid \theta) &= \frac{1}{\theta} \text{ for } 1/2 \leq \theta \leq 1 \end{align}$$

$$f_{\Theta}(\theta)=1$$

$$f_X(\frac{1}{2})=\int_{1}^{1/2}\frac{1}{\theta}=\ln (2)$$

$$f_{\Theta\mid X}(\theta \mid \frac{1}{2}=\frac{f_{X \mid \Theta}(\frac{1}{2} \mid \theta) f_\Theta(\theta)}{f_X(\frac{1}{2})}=\frac{1}{\theta \ln(2)} \text{ for } 1/2 \leq \theta \leq 1$$

On thier next date, Juliet arrives 1/4 hour late.
$$\Rightarrow 1/2 \leq \theta \leq 1$$

$$\begin{align}f_{\Theta\mid X_1 X_2}(\theta\mid 1/2,1/4) &\propto f_{X_1\mid \Theta}(1/2\mid \theta) f_{X_2\mid\Theta}(1/4\mid \theta)f_{\Theta}(\theta)\\ &= \frac{1}{\theta^2} \text{ for } 1/2 \leq \theta \leq 1 \end{align}$$

$$f_{\Theta\mid X_1 X_2}(\theta\mid 1/2,1/4) = \frac{\frac{1}{\theta^2}}{\int_{1/2}^1 \frac{1}{\theta^2} d\theta} = \frac{1}{\theta^2} \text{ for } 1/2 \leq \theta \leq 1 $$

On their first 3 dates, Juliet is late by 1/2, 1/4, 1/4 hours.
$$\Rightarrow 1/2 \leq \theta \leq 1$$

$$
\begin{align}
f_{\T | X_1 X_2 X_2}(\t | 1/2, 1/4, 1/4) 
&\propto 
f_{X_1| \T}(1/2 | \t)
f_{X_2| \T}(1/4 | \t)
f_{X_2| \T}(1/4 | \t)
f_\T(\t)\\
&=\frac{1}{\t^3} \text{ for } 1/2 \leq \theta \leq 1
\end{align}
$$

$$f_{\T | X_1 X_2 X_2}(\t | 1/2, 1/4, 1/4) = \frac{1/\t^3}{\int_{1/2}^1 \frac{1}{\t^3} d\t} = \frac{2}{3\t^3} \text{ for } 1/2 \leq \theta \leq 1$$

#### Lecture Example 2
Interarrival time of emails
Model:

$$\begin{align}X_1,...,X_n = \text{Exponential}(\T)\\
\T = \text{Exponential}(15)\end{align}$$

$$\begin{align}
f_{\T| X_1, ..., X_n}(\t |x_1,...,x_n) &\propto
f_{X_1|\Theta}(x_1|\theta)...f_{X_n|\T}(x_n|\t)f_\T(\t)\\
&=\t e^{-\t x_1}...\t e^{-\t x_n} \cdot 15e^{-15\t}\\
&\propto \t^n e^{-\t(x_1+...+x_n+15)}
\end{align}$$

Let $$s=x_1+...+x_n+15$$

$$f_{\T| X_1, ..., X_n}(\t |x_1,...,x_n)=\frac{\t^n\cdot e^{-s\t}}{\int_0^\infty {\t^n\cdot e^{-s\t}} dt}=\frac{s^{n+1}\cdot \t^n\cdot e^{-s\t}}{n!}$$

This is the p.d.f. of Erlang$$(s, n+1)$$ random variable.

More certain about the value of the parameter $$\T$$ as we have more samples.

![fx]({{ '/assets/images/unlisted/bayesian-inference.png' | relative_url }}){: style="width: 75%;" class="center"}

<br>
<h4>Homework 1.1</h4>
Alice is 50% sure that Bob's email address is `352642@acme.com`. She runs a test by sending sending 100 emails to random recipients of the form `abcdef@acme.com`. 95% of the emails bounce as undeliverable. Alice then sends an email intended for Bob to `352642@acme.com` and it does not bounce. What is the posterior probability that she correctly guessed his email address?

>$$A: $$ `352642@acme.com` is Bob's email\\
$$P(A)=P(A^C)=0.5$$\\
$$B: $$ Does not bounce.\\
$$P(B|A)=1$$\\
$$P(B|A^C)=0.05$$\\
$$P(A|B)=\frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^C)P(A^C)}=\frac{1\cdot 0.5}{1\cdot 0.5+0.05\cdot 0.5}\approx 0.952$$

<h4>Homework 1.2</h4>
After much dating experience, Romeo concludes that girls show up Exponential($\T$) hours late to a date, where $\T$ is a Uniform(0, 1) random variable that describes a girl’s type.

(a) Juliet is 10 minutes late on their first date. What is Romeo's posterior PDF for $\T$?

> $X$ ~ Exponential$(\T)$\\
$\T$ ~ Uniform(0,1)\\
$f_\T(\t)=1$\\
$f_{X|\T}(1/6|\t) = \t e^{-\t /6}$\\
$f_X(1/6)=\int_0^1 \t e^{-\t /6}d\t = 36-42e^{-1/6}$\\
$f_{\T | X}(\t | 1/6)=\frac{f_{X | \T}(1/6 | \t) f_{\T}(\t)}{f_X(1/6)}=\frac{\t e^{-\t/6}}{36-42e^{-1/6}} \text{ for } 0≤\t≤1$

(b) Juliet is 30 minutes late on their second date. What is Romeo’s posterior PDF now?
> $f_{\T \mid X_1 X_2}(\t \mid 1/6,1/2) \propto f_{X_1 \mid \T}(1/6 \mid \t) f_{X_2 \mid \T}(1/2 \mid \t) f_{\T}(\t)=\t^2 e^{-2\t/3}$ for $0≤\t≤1$\\
$f_{\T \mid X_1 X_2}(\t \mid 1/6, 1/2) = \frac{\t^2 e^{-2\t/3}}{\int_0^1 \t^2 e^{-2\t/3} d\t}$ for $0≤\t≤1$

#### Lecture Example 1.3

A Normal$(\T,1)$ RV take value $x=3.97$. What is posterior $\T$?

Prior: $\T$ is Normal$(0,1)$

$$\begin{align}
f_{\T\mid X}(\t \mid x) &\propto f_{X \mid \T}(x \mid \t) f_{\T}(\t)\\
&= e^{-(x-\t)^2/2} \cdot e^{-\t^2/2}\\
&\propto e^{-\frac{1}{2}(\t-x/2)^2/(1/\sqrt{2})^2}
\end{align}$$

Posterior: $(\T \mid x)$ is Normal$(x/2, 1/\sqrt{2})$

#### Lecture Example 1.4

Three independent Normal$(\T, 1)$ RVs takes values $3.97, 4.09, 3.11$. What is posterior $\T$?

Prior: $\T$ is Normal$(0,1)$

$$\begin{align}
f_{\T\mid X_1 X_2 X_3}(\t\mid x_1,x_2,x_3)&\propto f_{X_1\mid \T}(x_1\mid\t)f_{X_2\mid \T}(x_2\mid \t)f_{X_3\mid \T}(x_3\mid \t)f_{\T}(\t)\\
&\propto e^{-(x_1-\t)^2/2} e^{-(x_2-\t)^2/2} e^{-(x_3-\t)^2/2} e^{-x^2/2}\\
&\propto e^{-\frac{1}{2} (2\t-\frac{x_1+x_2+x_3}{2})^2}\\
&=e^-\frac{(\t-\frac{x_1+x_2+x_3}{4})^2}{2(\frac{1}{2})^2}\\
& \Rightarrow \text{Normal($\frac{x_1+x_2+x_3}{4}, \frac{1}{2}$)}
\end{align}$$