---
layout: post
title:  "On-policy Prediction with Approximation"
date:   2021-01-23 00:00
---

### Introduction
* Study the use of function approximation in approximating $v_\pi$ from experience generated using a known policy $\pi
\newcommand{\S}{\mathcal{S}}
\newcommand{\A}{\mathcal{A}}
\newcommand{\R}{\mathbb{R}}
\newcommand{\E}{\mathrm{E}}
\newcommand{\deq}{\dot{=}}
\newcommand{\argmax}[1]{\text{argmax}_{#1} \text{ }}
\newcommand{\eps}{\varepsilon}
\newcommand{\N}{\text{Normal}}
\newcommand{\p}{\rho}
\newcommand{\T}{\mathbb{T}}
\newcommand{\w}{\textbf{w}}
\newcommand{\v}{\hat{v}}
\newcommand{\VE}{\overline{\text{VE}}}
\newcommand{\sbar}{\bar{s}}
\newcommand{\pd}{\partial}
$.
* Approximate value function is represented by vector $\w \in \R^d$.
* Write $\v(s,\w)\approx v_\pi(s)$
* $\v$ may be a linear function in features of the state, with $\w$ the vector of the feature weights. 
* $\v$ may also be the function computed by a multi-layer ANN, with $\w$ the vector of connection weights in all the layers.

### 9.1 Value-function Approximation
* (Update notation) $s \mapsto u$: state $s$ to be updated, **update target** $u$ that $s$'s estimated value is shifted toward.
* MC update for value prediction: $S_t \mapsto G_t$
* TD(0) update: $S_t\mapsto R_{t+1}+\gamma \v(S_{t+1}, \w_t)$
* n-step TD update: $S_t \mapsto G_{t:t+n}$
* DP policy-evaluation update: $s \mapsto \E_\pi[R_{t+1}+\gamma \v(S_{t+1}, \w_t)\mid S_t=s]$
* Not all function approximation methods are equally well suited for use in RL. In RL, it is important that learning be able to occur online, while the agent interacts with its environment or with a model of its environment.
* Generally requires function approximation methods able to handle nonstationary target functions (target functions that change over time).

### 9.2 The Prediction Objective
* With function approximation, an update at one state affects many others, and it is not possible to get the values of all states exactly correct. Making one state's estimate more accurate invariably means making others' less accurate. We are obligated to say which states we care most about.
* State distribution representing how much we care about the error in each state $s$

$$\mu(s) \geq 0, \sum_s \mu(s)=1$$

* Error of a state $s$: difference between the approximate value $\v(s,\w)$ and the true value $v_\pi(s)$.
* The **Mean Squared Value Error**

$$\VE(\w)=\sum_{s\in \S}\mu(s)[v_\pi(s)-\v(s,\w)]^2$$

* **On-policy distribution**: $\mu(s)$ is chosen to be the fraction of time spent in $s$ in an episode under on-policy training.

$$\mu(s)=\frac{\eta(s)}{\sum_{s'}\eta(s')}, \text{ for all } s\in \S$$

$$\text{where }\eta(s)=h(s)+\sum_\sbar \eta(\sbar) \sum_a \pi(a\mid \sbar)p(s\mid \sbar,a)$$

* $h(s)$: probability that an episode begins in each state $s$
* $\eta(s)$: expected number of visits per episode
* $\sbar$: state preceding $s$

### 9.3 Stochastic-gradient and Semi-gradient Methods
* Gradient-descent methods: weight vector $\w=(w_1,...,w_d)^\top$
* $\v(s,\w)$ is a differentiable function of $\w$ for all $s\in \S$.
* Update $\w$ at each time step $t=0,1,2,...$ and let $\w_t$ denote the weight vector at each step.
* Assume for now we observe a new example $S_t\mapsto v_\pi(S_t)$ consisting of a state $S_t$ and its true value under the policy.
* Stochastic gradient-descent (SGD) methods minimize error $\VE$ by adjusting the weight vector after each example by a small amount in the direction that wouldmost reduce the error on that example:

$$\begin{align}
w_{t+1}&=w_t+\alpha[v_\pi(S_t)-\v(S_t,\w_t)]\nabla\v(S_t,\w_t)
\end{align}$$

$$\text{where }\nabla\v(s, \w)= \left (\frac{\pd\v(s, \w)}{\pd w_1}, ..., \frac{\pd\v(s, \w)}{\pd w_d} \right)^\top$$

* $\alpha$ should be decreasing.
* When the target output $U_t\in \R$ of the $t$-th training example, $S_t\mapsto U_t$, is not the true value, $v_\pi(S_t)$, but some approximation to it, we may substitute $U_t$ in place of $v_\pi(S_t)$.

$$w_{t+1}=w_t+\alpha[U_t-\v(S_t,\w_t)]\nabla\v(S_t,\w_t)$$

* If $U_t$ is an unbiased estimate, that is, if $\E[U_t\mid S_t=s]=v_\pi(S_t)$, for each $t$, then $\w_t$ is guaranteed to converge to a local optimum under the usual stochastic approximation conditions for decreasing $\alpha$.
* Monte Carlo target $U_t=G_t$ is unbiased estimate of $v_\pi(S_t)$. The gradient-descent version of MC state-value prediction is
![]({{ '/assets/images/unlisted/sgd-mc-state-value-prediction-pseudocode.png' | relative_url }}){: style="width: 100%;" class="center"}

* If a bootstrapping estimate of $v_\pi(S_t)$ is used as the target $U_t$, it is a biased estimate because it depends on $\w_t$. These are called **semi-gradient methods**.
* Semi-gradient TD(0) uses target $U_t=R_{t+1}+\gamma \v(S_{t+1}, \w)$
![]({{ '/assets/images/unlisted/semi-gradient-td0-pseudocode.png' | relative_url }}){: style="width: 100%;" class="center"}

<h3>References</h3>

1. Richard S. Sutton and Andrew G. Barto. Reinforcement Learning: An Introduction; 2nd Edition. 2017.