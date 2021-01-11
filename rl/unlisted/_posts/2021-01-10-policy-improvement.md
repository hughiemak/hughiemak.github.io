---
layout: post
title:  "Policy Improvement Theorem"
date:   2021-01-10
---
(Personal notes of Richard S. Sutton and Andrew G. Barto. Reinforcement Learning: An Introduction; 2nd Edition. 2017. p.78)

The policy improvement theorem states that if there are two determistic policies $$\pi$$ and $$\pi^\prime$$, and $$q_\pi(s, \pi^\prime(s)) \geq v_\pi(s) \text{ for all state } s \in \mathcal{S}$$, then $$v_{\pi^\prime}(s) \geq v_\pi(s) \text{ for all } s \in \mathcal{S}$$.

Furthermore, if $$q_\pi(s, \pi^\prime(s)) > v_\pi(s)$$ for some $$s \in \mathcal{S}$$, then $$v_{\pi^\prime}(s) > v_\pi(s)$$. In other words, policy $$\pi^\prime$$ is better than $$\pi$$.

Proof:

$$\begin{align}
v_\pi(s) &\leq q_\pi(s, \pi^\prime(s))\\
&= \mathbb{E}[R_{t+1} + \gamma v_\pi(S_{t+1}) \mid S_t=s, A_t=\pi^\prime(s)]\\
&= \mathbb{E}_{\pi^\prime}[R_{t+1} + \gamma v_\pi(S_{t+1})\mid S_t=s]\\
&\leq \mathbb{E}_{\pi^\prime}[R_{t+1} + \gamma q_\pi(S_{t+1}, \pi^\prime(S_{t+1})) \mid S_t=s]\\
&=\mathbb{E}_{\pi^\prime}[{R_{t+1} + \gamma{\mathbb{E}_{\pi^\prime}[{R_{t+2}+\gamma v_\pi(S_{t+2})}\mid {S_{t+1}, A_{t+1} = \pi^\prime (S_{t+1})}]}} \mid {S_t=s}]\\
&= \mathbb{E}_{\pi^\prime}[R_{t+1}+\gamma R_{t+2} + \gamma^2 v_\pi(S_{t+2})\mid S_t=s]\\
&\leq \mathbb{E}_{\pi^\prime}[R_{t+1}+\gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 v_\pi(S_{t+3}) \mid S_t=s]\\
&...\\
&\leq \mathbb{E}_{\pi^\prime}[R_{t+1}+\gamma R_{t+2} + \gamma^2 R_{t+3} + \gamma^3 R_{t+4} + ... \mid S_t=s]\\
&=v_{\pi^\prime}(s)
\end{align}$$
