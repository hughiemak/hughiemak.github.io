---
layout: post
title:  "Mathematics for Machine Learning (Deisenroth et al.)"
date: 2021-08-24
---

### Linear Algebra

#### Groups

Consider a set $\newcommand{\G}{\mathcal{G}}\G$ and an operation $\newcommand{\op}{\otimes}\op:\G\times\G\rightarrow\G$ defined on $\G$. Then $\G:=(\G,\op)$ is a group if the following hold:

1. Closure of $\G$ under $\op$: $\forall x, y\in \G: x \op y \in \G $
1. Associativity: $\forall x,y,z \in \G:(x \op y)\op z = x \op (y\op z)$
1. Neutral element: $\exists e \in \G$ such that $\forall x \in \G: x \op e = x$ and $e \op x= x$ 
1. Inverse element: $\forall x \in \G$, $\exists x^{-1}\in \G: x\op x^{-1}=e$ and $x^{-1}\op x=e$, where $e$ is the neutral element.

$G=(\G,\op)$ is an Abelian group if $\forall x, y \in \G: x\op y = y\op x$ (commutative).

#### Vector Spaces

A real-valued vector space $\newcommand{\V}{\mathcal{V}}V=(\V,+,\cdot)$ is a set $\V$ with two operations

$$+:\V\times \V \rightarrow \V$$

$$\newcommand{\R}{\mathbb{R}}\cdot : \R\times \V \rightarrow \V$$

where 

1. $(\V,+)$ is an Abelian group
1. Distributivity:
	1. $\forall \lambda \in \R, \newcommand{\x}{\boldsymbol{x}}
	\newcommand{\y}{\boldsymbol{y}} \x, \y \in \V, \lambda\cdot (\x+\y)=\lambda\cdot\x + \lambda\cdot\y$
	1. $\forall \lambda, \psi\in \R, \x\in \V:(\lambda+\psi)\cdot\x = \lambda \cdot \x + \psi\cdot \x$
1. Associativity (outer operation): $\forall \lambda, \psi\in \R, \x\in \V:\lambda\cdot(\psi\cdot \x)=(\lambda \psi)\cdot \x$
1. Neutral element with respect to the outer operation: $\forall \x\in \V:1\cdot \x = \x$

#### Vector Subspaces

$$\newcommand{\U}{\mathcal{U}}(\U,+,\cdot)$$ is a subspace of $V=(\V,+,\cdot)$ if 

1. $\newcommand{\0}{\boldsymbol{0}}\0\in\U$
1. $\forall \lambda\in \R, \forall \x \in \U: \lambda\x \in \U$.
1. $\forall \x, \y\in \U: \x + \y \in \U$.

### Matrix Decomposition

#### Determinant and Trace

- For any square matrix $\newcommand{\A}{\boldsymbol{A}}\A\in \R^{n\times n}$, $\A$ is invertible if and only if $\|A\|\neq 0$.

- For any triangular matrix $\newcommand{\T}{\boldsymbol{T}}\T\in\R^{n\times n}$, the determinant is the product of the diagonal elements.

- A square matrix $\A\in \R^{n\times n}$ has $\|\A\|\neq 0$ if and only if $rank(\A)=n$, i.e., $\A$ is invertible if and only if it is full rank.

- The trace of a square matrix $\newcommand{\nxn}{n \times n} \A\in\R^{\nxn}$ is defined as

$$\newcommand{\tr}{\text{tr}}\tr(\A):=\sum_{i=1}^n a_{ii}$$

- Trace properties:
	- $\newcommand{\B}{\boldsymbol{B}}\tr(\A+\B) = \tr(\A) + \tr(\B)$ for $\A,\B \in \R^{\nxn}$
	- $\tr(\alpha \A) = \alpha \tr(A), \alpha \in \R$ for $\A\in R^{\nxn}$
	- $\newcommand{\I}{\boldsymbol{I}} \tr(\I_n) = n$
	- $\tr(\A\B)=tr(\B\A) for \A\in\R^{n\times k}, \B\in \R^{k\times n}$
	- The trace is invariant under cyclic permutations. e.g.
	$\newcommand{\K}{\boldsymbol{K}}\newcommand{\L}{\boldsymbol{L}}\tr(\A\K\L)=\tr(\K\L\A)$ and $\tr(\x\y^T)=\tr(\y^T\x)=\y^T\x\in \R$.

- Charactersitic Polynomial. For $\lambda\in\R$ and a square matrix $\A\in\R^{\nxn}$

$$\begin{align*}p_\A(\lambda)&:=|\A-\lambda\I|\\
&=c_0+c_1\lambda+c_2\lambda^2 + ...c_{n-1}\lambda^{n-1}+(-1)^n\lambda^n
\end{align*}$$

where $c_0,...,c_{n-1}\in R$ is the characteristic polynomial of $\A$. In particular,

$$c_0=|\A|$$

$$c_{n-1}=(-1)^{n-1}\tr(\A)$$

#### Linear Independence

- Consider a vector space $V$ and a finite number of vectors $\x_1,..., \x_k\in V$. Then every $\newcommand{\v}\{\boldsymbol{v}}\v\in \V$ of the form

$$\v=\lambda_1\x_1+...+\lambda_k\x_k = \sum_{i+1}^k \lambda_i\x_i$$ 

with $\lambda_1, ..., \lambda_k\in \R$ is a linear combination of the vector $\x_1,...,\x_k$.

- Linear Independence: If there is a non-trivial linear combination, such that $\0=\sum_{i=1}^k \lambda_i\x_i$ with at least one $\lambda_i\neq 0$, the vectors $\x_1,...,\x_k$ are linearly dependent. If only trivial solution $\lambda_1=...=\lambda_k=0$ exists, the vectors are linearly independent.

#### Linear Mappings

- For vector spaces $V,W$, a mapping $\Phi: V\rightarrow W$ is called a linear mapping if 

$$\forall \x, \y \in V, \forall \lambda,\psi \in \R: \Phi(\lambda\x+\psi\y)=\lambda\Phi(\x)+\psi\Phi(\y)$$

- Injective, surjective, bijective. Consider a mapping $\Phi: V\rightarrow W$, where $V,W$ can be arbitrary sets
. Then $\Phi$ is called
	- Injective  if $\forall \x,\y\in V: \Phi(\x)=\Phi(\y)\Longrightarrow \x = \y$.
	- Surjective if $\Phi(V)=W$.
	<!--  -->

- Special cases of linear mappings
	- Isomorphism: $\Phi: V\rightarrow W$ linear and bijective
	- Endomorphism: $\Phi:V\rightarrow V$ linear
	- Automophism: $\Phi: V\rightarrow V$ linear and bijective
	- $\newcommand{\id}{\text{id}} \id_V: V\rightarrow V, \x \mapsto \x$ as the identity mapping.

- Finite-dimensional vector spaces $V$ and $W$ are isomorphic if and only if $dim(V)=dim(W)$.
	- i.e. There exists a linear, bijective mapping between two vector spaces of the same dimension.

- Basis Change: For a linear mapping $\Phi:V\rightarrow W$, ordered bases

$$\newcommand{\b}{\boldsymbol{b}}B=(\b_1,..., \b_n), \tilde{B}=(\tilde{\b_1},..., \tilde{\b_n})$$

of $V$ and

$$\newcommand{\c}{\boldsymbol{c}}C=(\c_1,..., \c_m), \tilde{C}=(\tilde{\c_1},..., \tilde{\c_m})$$

of $W$, and a transformation matrix $\A_\Phi$ of $\Phi$ with respect to $B$ and $C$, the corresponding transformation matrix $\tilde{\A}$ with respect to the bases $\tilde{B}$ and $\tilde{C}$ is given as 

$$\newcommand{\S}{\boldsymbol{S}} \tilde{\A}_\Phi=\T^{-1}\A_\Phi \S.$$

where $\S\in \R^{\nxn} $ is a transformation matrix of $\id_V$ that maps coordinates with respect to $\tilde{B}$ onto coordinates with respect to $B$, and $\T\in \R^{m\times m}$ is the transformation matrix of $\id_W$ that maps coordinates with respect to $\tilde{C}$ onto coordinates with respect to $C$.

- Equivalence: Two matrices $\A, \tilde{\A}\in \R^{\nxn}$ are equivalent if there exists regular matrices $\S\in \R^{\nxn}$ and $\newcommand{\T}{\boldsymbol{T}}\T \in \R^{m \times m}$ such that $\tilde{\A}=\T^{-1}\A\S$.

- Similarity: Two matrices $\A, \tilde{\A}\in \R^{\nxn}$ are similar if there exists a regular matrix $\S\in \R^{\nxn}$ with $\tilde{\A}=\S^{-1}\A\S$.

#### Eigenvalues and Eigenvectors

- Let $\A\in \R^{\nxn} $ be a square matrix. Then $\lambda \in \R$ is an eigenvalue of $\A$ and $\x \in \R^n \backslash\\{ \0 \\}$ is the corresponding eigenvector of $\A$ if

$$\A\x=\lambda\x$$

- These statements are equivalent:
	- $\lambda$ is an eigenvalue of $\A\in \R^{\nxn}$.
	- There exists and $\x\in \R^n\backslash\\{\0\\}$ with $\A\x=\lambda\x$, or equivalently, $(\A-\lambda\I_n)\x = \0$ can be solved non-trivially, i.e. $\x\neq \0$.
	- $rank(\A-\lambda\I_n)< n$.
	- $\|\A-\lambda\I_n\|=0$.

<!-- - Collinearity and Codirection: Two vectors that point in the same direction are called codirected. Two vectors are collinear if they point in the same or the opposite direction.

- If $\x$ is an eigenvector of $\A$ associated with eigenvalue $\lambda$, all vectors that are collinear to $\x$ are also eigenvectors. -->

- $\lambda \in \R$ is an eigenvalue of $\A\in \R^{\nxn}$ if and only if $\lambda$ is a  root of the characteristics polynomial $p_A(\lambda)$ of $\A$.

- Let $\A$ have an eigenvalue $\lambda_i$. The algebraic multiplicity of $\lambda_i$ is the number of times the root appears in the characteristic polynomial.

- Eigenspace and Eigenspectrum. For $\A\in\R^{\nxn}$, the set of all eigenvectors of $\A$ associated with an eigenvalue $\lambda$ spans a subspace of $R^n$, which is called the eigenspace of $\A$ with respect to $\lambda$ and is deonted by $E_\lambda$. The set of all eigenvalues of $\A$ is called the eigenspectrum of $\A$.

- $\A$ and $\A^T$ share the same eigenvalues but not necessarily the same eigenvectors.

- The eigenspace $E_\lambda$ is the null space of $\A -\lambda\I$ since 

$$\A\x=\lambda\x \Longleftrightarrow \A\x-\lambda\x = \0 \Longleftrightarrow (\A-\lambda\I)\x=\0$$

- Similar matrices possess the same eigenvalues.

- Symmetric, positive definite matrices always have positive, real eigenvalues.

- Geometric multiplicity: Let $\lambda_i$ be an eigenvalue of a square matrix $\A$. Then the grometric multiplicity of $\lambda_i$ is the number of linearly independent eigenvectors associated with $\lambda_i$.