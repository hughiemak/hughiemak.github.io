---
layout: post
title:  "Strong Induction"
date:   2021-02-2
category: discrete_maths
---
<div class=box2>
Prove that $$\forall n \geq 12, \$n $$ can be formed by $$\$4$$ and $$\$5$$
{: style="text-align:center;"}
</div>

Let $P(n)$ be the statement that $$$n$$ can be formed by $$$4$$ and $$$5$$.

Base cases: 

$$\begin{align}
12 &=4+4+4\\
13 &=4+4+5\\
14 &= 5+5+4\\
15 &=5+5+5
\end{align}$$

Inductive step: 

Assume $P(j)$ is true for $12 \leq j \leq k$ and $k\geq 15$. When $n=k+1$,

$$k+1=k-3+4$$

By inductive hypothesis, $P(k-3)$ is true. So $P(k+1)$.

Therefore, $\forall n \geq 12, P(n)$.