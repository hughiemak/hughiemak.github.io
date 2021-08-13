---
layout: post
title:  "Analysis I"
date:   2021-01-13 00:02
---
<h3>Chapter 1: Introduction</h3>
<h4>1.1 What is analysis?</h4>

Real analysis: the analysis of the real numbers, sequences and series of real numbers, and real-valued functions. 

#### 1.2 Why do analysis?

One can get into trouble if one applies rules without knowing where they came from and what the limits of their applicability are. Some examples in which several familiar rules, if applied blindly without knowledge of the underlying analysis, can lead to disaster.
* Division by zero
* Divergent series
* Divergent sequences
* Limiting values of functions
* Interchanging sums
* Interchanging integrals
* Interchanging limits
* Interchanging limits and integrals
* Interchanging limits and derivatives
* Interchanging derivatives
* L'Hopital's rule
* Limits and lengths

As you learn analysis you will develop an "analytical way of thinking", which will help you whenever you come into contact with any new rules of mathematics, or when dealing with situations which are not quite covered by the standard rules.(13)

You will develop a sense of why a rule in mathematics works, how to adapt it to new situations, and what its limitations are; this will allow you to apply the mathematics you have already learnt more confidently and correctly.(13)

<h3>Chapter 2: Starting at the beginning: the natural numbers</h3>

>Why do the rules of algebra work at all?

>How does one actually define the natural numbers?

#### 2.1 The Peano axioms

<u>Definition 2.1.1</u> (Informal) 

A natural number is any element of the set $$\newcommand{\pp}{\texttt{++}} N := \{ 0,1,2,... \}$$

<div class="box">
<u>Axiom 2.1 

$0$ is a natural number
</div>
<div class="box">
<u>Axiom 2.2 

If $n$ is a natural number, then $n\pp$ is also a natural number.
</div>
<div class="box">
<u>Definition 2.1.3 

$1:=0\pp, 2:=1\pp, 3:=2\pp, ...$
</div>
<u>Proposition 2.1.4

$3$ is a natural number.
<div class="box2">
Proof\\
By Axiom 2.1, $0$ is a natural number. By Axiom 2.2, $0\pp=1$ is a natural number. By Axiom 2.2 again, $1\pp=2$ is a natural number. By Axiom 2.2 again, $2\pp=3$ is a natural number.
</div>
<div class="box">
<u>Axiom 2.3 

$0$ is not the successor of any natural number; *i.e.* we have $n\pp \neq 0$ for every natural number $n$.
</div>
<u>Proposition 2.1.6 

$4$ is not equal to $0$.
<div class="box2">
Proof\\
$4=3\pp\neq 0$ by Axiom 2.3.
</div>
<div class="box">
<u>Axiom 2.4 

Different natural numbers must have different successors; *i.e.*, if $n,m$ are natural numbers and $n\neq m$, then $n\pp\neq m\pp$. Equivalently, if $n\pp=m\pp$, then we must have $n=m$.
</div>
<u>Proposition 2.1.8

$6$ is not equal to $2$.
<div class="box2">
Proof\\
Suppose $6=2$. Then $5\pp=1\pp$ so by Axiom 2.4 $5=1$, so that $4\pp=0\pp$. By Axiom 4.2 again we have $4=0$, contradicting proposition 2.1.6.
</div>
<div class="box">
<u>Axiom 2.5</u> (Principle of mathematical induction)

Let $P(n)$ be any property pertaining to a natural number $n$. Suppose that $P(0)$ is true, and that whenever $P(n)$ is true, $P(n\pp)$ is also true. Then $P(n)$ is true for every natural number $n$.
</div>
<div class="box">
<u>Axiom 2.6

There exists are number system $N$, whose elements we will call natural numbers, for which Axioms 2.1-2.5 are true.
</div>
<u>Remarks
* A remarkable accomplishment of modern analysis is that just by starting from these five very primitive axioms, and some additional axioms from set theory, we can build all the other number systems, create functions, and do all the algebra and calculus that we are used to.
* One interesting feature about the natural numbers is that while each individual natural number is finite, the set of natural numbers is infinite.
* This is how mathematics works- it treats its objects abstra~tly, caring only about what properties the ob- jects have, not what the objects are or what they mean.
* Historically, the realization that numbers could be treated axiomatically is very recent, not much more than a hundred years old. Before then, numbers were generally under- stood to be inextricably connected to some external concept.

<u>Proposition  2.1.16</u> (Recursive definitions)

Suppose for each natural number $n$, we have some function $f_n: N\rightarrow N$ from the natural numbers to the natural numbers. Let $c$ be a natural number. Then we can assign a unique natural number $a_n$ to each natural number $n$, such that $a_0=c$ and $a_{n\pp}=f_n(a_n)$ for each natural number $n$.

<div class="box2">
Proof\\
(See p.26)
</div>

#### 2.2 Addition
<div class="box">
<u>Definition 2.2.1</u> (Addition of natural numbers)

Let $m$ be a natural number. To add zero to $m$, we define $0+m := m$. Suppose inductively that we have defined how to add $n$ to $m$. Then we can add $n\pp$ to $m$ by defining $(n\pp)+m:=(n+m)\pp$
</div>
<div class="box2">
Example\\
$2+3=(1\pp)+3=(1+3)\pp=(3\pp)\pp=4\pp=5$
</div>
<div class="box">
<u>Lemma 2.2.2 

For any natural number $n$, $n+0=n$.
</div>
<div class="box2">
Proof

Base case $n=0$: $0+n=0+0=0=n+0$

Suppose inductively that $n+0=n$, want to show $(n\pp)+0=n\pp$

By the definition of addition, $(n\pp)+0 = (n+0)\pp=n\pp$
</div>
<div class="box">
<u>Lemma 2.2.3

For any natural numbers $n$ and $m$, $n+(m\pp)=(n+m)\pp$.
</div>
<div class="box2">
Proof

Base case: $0+(m\pp)=(0+m)\pp$

Inductive step: Suppose $n+(m\pp)=(n+m)\pp$. Want to show $(n\pp)+(m\pp)=((n\pp)+m)\pp$

$$
\scriptsize
\begin{align}
(n\pp)+(m\pp)&=(n+(m\pp))\pp && \text{by addition definition}\\
&=((n+m)\pp)\pp && \text{by inductive hypothesis}\\
&=((n\pp)+m)\pp && \text{by addition definition}
\end{align}$$

</div>

<div class="box">
Corollary of Lemma 2.2.2 and Lemma 2.2.3

$$n\pp=n+1$$
</div>

<u>Proposition 2.2.4</u> (Addition is commutative)

For any natural numbers $n$ and $m$, $n+m=m+n$.

<div class="box2">
Keeping $n$ fixed.

Base case: $0+m=m=m+0$ 

Inductive step: Suppose $n+m=m+n$.. Want to show $(n\pp)+(m\pp)=(m\pp)+(n\pp)$.

$$
\scriptsize
\begin{align}
(n\pp)+m&=(n+m)\pp && \text{by addition definition}\\
&= (m+n)\pp &&\text{by inductive hypothesis}\\
&= m+(n\pp) &&\text{by Lemma 2.2.3}
\end{align}
$$

</div>

<u>Proposition 2.2.5</u> (Addition is associative)

For any natural numbers $a,b,c$, we have $(a+b)+c=a+(b+c)$.

<u>Proposition 2.2.6</u> (Cancellation law)

Let $a,b,c$ be natural numbers such that $a+b=a+c$. Then we have $b=c$.

<div class="box2">
Proof

Base case ($a=0$): $0+b=0+c$ so $b=c$ by addition definition.

Inductive step: Suppose $a+b=a+c \Rightarrow b=c$. Want to show $(a\pp)+b=(a\pp)+c \Rightarrow b=c$. Assume $(a\pp)+b=(a\pp)+c$,

$$
\scriptsize
\begin{align}
(a\pp)+b=(a+b)\pp && \text{by addition definition}\\
(a\pp)+c=(a+c)\pp && \text{by addition definition}\\
\Rightarrow (a+b)\pp=(a+c)\pp\\
\Rightarrow (a+b)=(a+c) && \text{by Axiom 2.4}\\
\Rightarrow a=c && \text{by inductive hypothesis}
\end{align}$$ 

</div>

<div class="box">
<u>Definition 2.2.7</u> (Positive natural numbers)

A natural number $n$ is said to be positive iff it is not equal to $0$.
</div>

<u>Proposition 2.2.8</u>

If $a$ is positive and $b$ is a natural number, then $a+b$ (and $b+a$) is positive.

<div class="box2">
Proof

Base case ($b=0$): $a+b=a+0=a$, which is positive. 

Inductive step: Suppose $a+b$ is positive. Then $a+(b\pp)=(a+b)\pp \neq 0$ (positive) by Axiom 2.3. 
</div>

<u>Corollary 2.2.9</u>

If $a$ and $b$ are natural numbers such that $a+b=0$, then $a=0$ and $b=0$.

<div class="box2">
Proof

If $a\neq 0$, $a$ is positive and by proposition 2.2.8 $a+b=0$ is positive, a contradiction.

If $b\neq 0$, $a$ is positive and by proposition 2.2.8 $a+b=0$ is positive, a contradiction.

Thus, $a$ and $b$ must both be 0.
</div>

<div class="box">
<u>Lemma 2.2.10</u>

Let $a$ be a positive number. Then there exists exactly one natural number $b$ such that $b\pp=a$
</div>

<div class="box">
<u>Definition 2.2.11</u> (Ordering of the natural numbers)

Let $n$ and $m$ be natural numbers. We say that $n$ is greater than or equal to $m$, and write $n \geq m$ or $m \leq n$, iff we have $n = m + a$ for some natural number $a$. We say that $n$ is strictly greater than $m$, and write $n > m$ or $m < n$, iff $n \geq m$ and $n \neq m$.
</div>

Note that there is no largest natural number $n$, because the next number $n\pp$ is always larger than $n$.

<div class="box">
<u>Proposition 2.2.12</u> (Basic properties of order for natural numbers). 

Let $a,b,c$ be natural numbers. Then

1. (Order is reflexive) $a\geq a$.
1. (Order is transitive) If $a\geq b$ and $b\geq c$, then $a\geq c$.
1. (Order is anti-symmetric) If $a\geq b$and $b\geq a$, then $a=b$.
1. (Addition preserves order) $a\geq b$ iff $a+c\geq b+c$
1. $a < b$ iff $a\pp \leq b$.
1. $a < b$ iff $b=a+d$ for some positive number $d$.
</div>

