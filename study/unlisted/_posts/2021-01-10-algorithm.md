---
layout: post
title:  "Algorithm"
date:   2021-01-11 00:01
---
1. Algorithmics: Design and analysis of algorithms.

1. Algorithmic problem $$\Pi$$: A specificication of all legal inputs $$I_\Pi$$, and a function $$f_\Pi: I_\Pi \rightarrow O_\Pi$$ that maps each input $$i \in I_\Pi$$ to its output $$f_\Pi(i) \in O_\Pi$$.

1. Algorithm: A finite sequence of basic instructions for solving algorithmic problem (i.e., computing $$f_\Pi(i)$$ for each legal input $$i$$) that terminates in a finite number of steps. The underlying mathematical model for an algorithm is a Turing machine program.

1. Correctness: Algorithm $$\def \A {\mathcal{A}} \A$$ solves problem $$\Pi$$ if for every legal input $$i$$ to $$\A$$, the algorithm terminates in a finite number of steps and produces $$f_\Pi (i)$$ as the output.

1. Incorrect behavior of an algorithm: (a) Terminates normally but with wrong output, (b) doesn't terminate, and (c) aborts execution abnormally.

1. Partial correctness: For every legal input $$i$$, once $$\A$$ terminates, $$\A$$ correctly produces $$f_\Pi(i)$$ as output. 

1. Total correctness: $$\A$$ is partially correct and $$\A$$ terminates for all legal inputs.

1. Three main concerns: Correctness (need to be proved mathematically), efficiency (Time and space), simplicity (easy to understand).

<hr>
<br>

<b>1.8. Reverse edges to obtain an acyclic digraph. </b>
{% highlight pseudocode%}
while G contains a directed cycle C do
    Choose an edge e in C and reverse the direction of e.
end while
{% endhighlight %}
Partial correctness is obvious because $$G$$ has no directed cycle when the algorithm stops. But it may not terminate at all so it is not a correct algorithm.
<br>
<br>
<b>1.9. The $$3x+1$$ problem. It is unknown whether it halts for all positive integers $$x$$.</b>
{% highlight pseudocode%}
while x > 1 do
    if x is even then x ← x/2
                 else x ← 3x+1;
end while
{% endhighlight %}
<br>
<b>1.10 Fibonacci number: $f_0=0,f_1=1$ and $f_n=f_{n-1}+f_{n-2}$ for $n≥2$.</b>
{% highlight pseudocode%}
function f(n) 
    if n=0, return 0.
    if n=1, return 1.
    otherwise return f(n-1)+f(n-2)
{% endhighlight %}
Recursion is slow with runing time = O($1.618^n$).
{% highlight pseudocode%}
F[0,...,n]
for i=1 to n do
    F[n] ← F[n-1] + F[n-2]
{% endhighlight %}
Iteration has good time but space is not so good.
{% highlight pseudocode%}
On input n,
    x ← 1, y ← 0
    for i = 1 to n do
        y ← x+y
        x ← y-x
    end for
    print y
{% endhighlight %}
Correctness: The algorithm terminates after $n$ iterations. We need to prove that $y$ contains the value of $f_n$ when the algorithm terminates.

Let $x_i, y_i$ be the values of $x$ and $y$ after $i$-th iteration.

Invariant: After $i$-th iteration, $y_i=f_i$ and $x_i=f_{i-1}$.

Prove by induction: 

Base case: $y_0=f_{0}=0$, $x_0=f_{-1}=1$

Inductive step: Suppose after $i$-th iteration, $y_i=f_i$ and $x_i=f_{i-1}$. Then after the $(i+1)$-th iteration, $y_{i+1}=x_i+y_i=f_{i-1}+f_i=f_{i+1}$ and $x_{i+1}=y_{i+1}-x_{i}=f_{i+1}-f_{i-1}=f_i$.
<br>
<br>
<b>1.11. Multiplication: compute the product of two non-negative integers $$x$$ and $$y$$.</b>
{% highlight pseudocode%}
p ← 0;
while x > 0 do
    if x is odd then p ← p+y;
    x ← floor(x/2);
    y ← 2y;
end while;
print p
{% endhighlight %}

Proof:
Let $x_i$, $y_i$ and $p_i$ be values of $x$, $y$ and $p$ after $i$-th iteration. We claim that for all $i≥0$, $xy=p_i+x_iy_i$ is an invariant. So when the algorithm terminates after the $i^* $-th iteration, $x^* =0$ and therefore $p^* =xy$. We use induction to establish this claim.

When $i=0$, then $p_0=p$, $x_0=x$, $y_0=y$ so $xy=p_i+x_iy_i$. 

Assume that $xy=p_i+x_iy_i$ for some $i≥0$. After the $(i+1)$-th iteration,

Case 1: $x_{i}$ is even. 
$$
\begin{cases}
p_{i+1}=p_{i}\\
x_{i+1}=x_{i}/2\\
y_{i+1}=2y_{i}
\end{cases}\\
\Rightarrow xy=p_{i+1}+x_{i+1}y_{i+1}
$$

Case 2: $x_{i}$ is odd.
$$
\begin{cases}
p_{i+1}=p_{i}+y_i\\
x_{i+1}=(x_{i}-1)/2\\
y_{i+1}=2y_{i}
\end{cases}\\
\Rightarrow xy=p_{i+1}+x_{i+1}y_{i+1}
$$ 


<!-- > $p \leftarrow 0;$
> while x > 0 do
$\quad$ if $x$ is odd then $p \leftarrow p+y;$ -->


<!-- > Algorithm parameters: step size  $\alpha \in (0 , 1] , \epsilon > 0$   
Initialize  $Q  ( s, a ), \  \forall s \in S^+ , a \in A ( s ),$ arbitrarily except that $Q ( terminal , \cdot ) = 0$    
>
> Loop for each episode:  
$\quad$Initialize $S$   
$\quad$Loop  for  each  step  of  episode:    
$\qquad$Choose  $A$ from $S$ using some policy derived from $Q$ (eg $\epsilon$-greedy)   
$\qquad$Take action $A$, observe $R, S'$   
$\qquad Q(S,A) \leftarrow Q(S,A) + \alpha[R+\gamma \max_a(S', a) - Q(S, A)]$   
$\qquad S \leftarrow S'$    
$\quad$ until $S$ is terminal -->

<!-- <pre id="algo" style="display:hidden;">
    % This quicksort algorithm is extracted from Chapter 7, Introduction to Algorithms (3rd edition)
    \begin{algorithm}
    \caption{Quicksort}
    \begin{algorithmic}
    \PROCEDURE{Quicksort}{$A, p, r$}
        \IF{$p < r$} 
            \STATE $q = $ \CALL{Partition}{$A, p, r$}
            \STATE \CALL{Quicksort}{$A, p, q - 1$}
            \STATE \CALL{Quicksort}{$A, q + 1, r$}
        \ENDIF
    \ENDPROCEDURE
    \PROCEDURE{Partition}{$A, p, r$}
        \STATE $x = A[r]$
        \STATE $i = p - 1$
        \FOR{$j = p$ \TO $r - 1$}
            \IF{$A[j] < x$}
                \STATE $i = i + 1$
                \STATE exchange
                $A[i]$ with $A[j]$
            \ENDIF
            \STATE exchange $A[i]$ with $A[r]$
        \ENDFOR
    \ENDPROCEDURE
    \end{algorithmic}
    \end{algorithm}
</pre> -->
