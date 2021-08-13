---
layout: post
title:  "A Course in Game Theory -  Martin J. Osborne and Ariel Rubinstein"
date:   2021-01-15 00:00
---

### Introduction
#### 1.1 Game Theory
* Tools designed to help us understand the phenomena that we observe when decision-makers interact.
* Decision-makers are rational: pursue well-defined exogenous objectives
* Decision-makers reason strategically: take into account their knowledge or expectations of other decision-makers’ behavior

#### 1.2 Games and Solutions
* A game is a description of strategic interaction that includes the constraints on the actions that the players can take and the players’ interests, but does not specify the actions that the players do take.
* A solution is a systematic description of the outcomes that may emerge in a family of games.
* Game theoretic models: strategic games, extensive games with and without perfect information, and coalitional games
* Player: an individual or as a group of individuals making a decision
* Noncooperative Games: the sets of possible actions of individual players are primitives
* Coorperative Games: the sets of possible joint actions of groups of players are primitives
* Strategic game: each player chooses his plan of action once and for all, and all players’ decisions are made simultaneously
* Extensive game: each player can consider his plan of action not only at the beginning of the game but also whenever he has to make a decision
* Games with perfect information: participants are fully informed about each others’ moves
* Games with imperfect information: participants may be imperfectly informed

#### 1.3 Game Theory and the Theory of Competitive Equilibrium
* Game theoretic reasoning takes into account the attempts by each decision-maker to obtain, prior to making his decision, information about the other players’ behavior.
* Competitive reasoning assumes that each agent is interested only in some environmental parameters (such as prices), even though these parameters are determined by the actions of all agents.

#### 1.4 Rational Behavior
* Each decision-maker is “rational” in the sense that he is aware of his alternatives, forms expectations about any unknowns, has clear preferences, and chooses his action deliberately after some process of optimization.
* Model of rational choice
	* A set $A$ of actions from which the decision-maker makes a choice.
	* A set $C$ of possible consequences of these actions.
	* A consequence function $g:A \rightarrow C$ that associates a consequence with each action.
	* A preference relation $\newcommand {\ssss} {\succsim} \ssss$ on the set $C$.
* Sometimes the decision-maker’s preferences are specified by giving a utility function $U: C \rightarrow \mathbb{R}$, which defines a peference relation $\ssss$ if and only if $U(x) ≥ U(y)$.
* $B \subseteq A$: feasible actions
* A rational decision-maker chooses an action $a^* \in B$ that is optimal in the sense that $g(a^* ) \ssss g(a), \forall a \in B$.
* The player always uses the same preference relationd when choosing from different sets $B$.
* If the consequence function is stochastic and known to the decision-maker, then the decision-maker is assumed to behave as if he maximizes the expected value of a function that attaches a number to each consequence.
* If the stochastic connection between actions and consequences is not given, the decision-maker is assumed to behave as if he has in mind a subjective probability distribution that determines the consequence of any action.
* The decision-maker is assumed to behave as if he has in mind a "state space" $\Omega$, a probability measure over $\Omega$, a function $g: A\times \Omega \rightarrow C$, and a utility function $u: C\rightarrow \mathbb{R}$, and choose an action $a$ that maximizes the expected value of $u(g(a, \omega))$ w.r.t. the probability measure.

#### 1.5 The Steady State and Deductive Interpretations
* Steady state interpretation: treats a game as a model designed to explain some regularity observed in a family of similar situations.
* Deductive interpretation: treats a game in isolation, as a “one-shot” event, and attempts to infer the restrictions that rationality imposes on the outcome; it assumes that each player deduces how the other players will behave simply from principles of rationality.

#### 1.6 Bounded Rationality
* The abstract model of chess allows use to deduce a significant fact about the game, but at the same time it omits the most important determinant of the outcome of an actual play of chess: the players’ “abilities”.
* Modeling asymmetries in abilities and in perceptions of a situation by different players is a fascinating challenge for future research, which models of “bounded rationality” have begun to tackle.

#### 1.7 Terminology and Notation
* $N$: the set of players
* Profile
	* A collection of values of some variable, one for each player
	* Denoted by $(x_i)$ or $(x_i)_{i\in N}$
* $x_{-i}=$ $$(x_j)_{ j\in N \backslash \{ i \} }$$
* $(x_{-i}, x_i)$: the profile $(x_i)_{i\in N}$
* A peference relation $\ssss$
	* complete ($\forall a, b\in A, a \ssss b$ or $b\ssss a$)
	* reflexive ($\forall a \in A, a\ssss a$)
	* transitive ($\forall x,y,z \in A$, if $x \ssss y$ and $y\ssss z$ then $x \ssss z$)
* $a \succ b$ if $a \ssss b$ but not $b\succsim a$
* $a \sim b$ if $a \ssss b$ and $b\ssss a$
* A preference relation $\ssss$ on $A$ is continuous if $a \ssss b$ whenever there are sequences $(a^k)_k$ and $(b^k)_k$ in $A$ that converge to $a$ and $b$ respectively for which $a^k \ssss b^k$ for all $k$.
* A preference relation $\ssss$ on $\mathbb{R}^n$ is quasi-concave if for every $b\in \mathbb{R}^n$ the set $$\{a \in \mathbb{R}^n: a \ssss b\}$$ is convex; it is strictly quasi-concave if every such set is strictly convex.
* Let $X\subseteq \mathbb{R}^N$ be a set. $x\in X$ is Pareto efficient if there is no $y\in X $ for which $y_i>x_i$ for all $i\in N$; $x\in X$ is strongly Pareto efficient if there is no $y\in X$ for which $y_i≥x_i$ for all $i\in N$ and $y_i>x_i$ for some $i\in N$.

![fx]({{ '/assets/images/unlisted/pareto-efficient.jpg' | relative_url }}){: style="width: 70%;" class="center"}

* A probability measure $\mu$ on a finite (or countable) set $X$ is an additive function that associate a nonnegative real number with every subset of $X$ (that is, $\mu(B\cup C)=\mu(B)+\mu(C)$ whenever $B$ and $C$ are disjoint) and satisfies $\mu(X)=1$.

### Nash Equilibrium

#### 2.1 Strategic Game
* A strategic game is a model of interactive decision-making in which each decision-maker chooses his plan of action once and for all, and these choices are made simultaneously.
* An action profile $a=(a_j)_{j\in N}$ is an outcome
* $A$: the set $$\times_{j\in N} A_j=\{ A_1,...,A_N \}$$ of outcomes
* The strategic game model $<N, (A_i), (\ssss_i)>$
	* a finite set $N$ of players
	* for each player $i\in N$ a nonempty set $A_i$
	* for each player $i\in N$ a preference relation $\ssss_i$ on $$A=\times_{j\in N}A_j=\{A_1, ..., A_N\}$$
* If the set $A_i$ of actions of every player $i$ is finite then the game is finite.
* Sometimes, players' preferences are most naturally defined over their consequences.
	* a set of consequences $C$ 
	* a function $g: A\rightarrow C$
	* a profile $(\ssss_i^* )$ of preference relations over $C$
	* Define $a \ssss_i b$ if and only if $g(a)\ssss_i^* g(b)$
* In some situaions, the consequence of an action profile is affected by an exogenous random variable whose realization is not known to the players before they take their actions.
	* a a set of consequences $C$ 
	* a function $g: A \times \Omega \rightarrow C$.
	* $g(a,w)$: the consequence when the action profile is $a\in A$ and the realization of the random variable is $\omega\in \Omega$
	* A profile of actions induces a lottery on $C$; for each player $i$ a preference relation $\ssss_i^* $ must be specified over the set of all such lotteries.
	* Define $a \ssss_i b$ if and only if $g(a, \cdot) \ssss_i^* g(b, \cdot)$.
* Payoff function $u_i: A\rightarrow \mathbb{R}$
	* $u_i(a)≥u_i(b)$ whenever $a\ssss_i b$
	* Payoffs: values of the function
	* Denote the game by $<N, (A_i), (u_i)>$

![fx]({{ '/assets/images/unlisted/2-player-strategic-game-representation.png' | relative_url }}){: style="width: 80%;" class="center"}

* For a situation to be modeled as a strategic game it is important only that the players make decisions independetly, no player being informed of the choice of any other player prior to making his own decision.

#### 2.2 Nash Equilibrium
* (DEFINITION 14.1) A Nash equilibrium of a strategic game $<N, (A_i), (\ssss_i)>$ is a  profile $a^* \in A$ of actions with the property that for every player $i\in N$ we have

$$(a_{-i}^* , a_i^* )\ssss_i (a_{-i}^* , a_i) \text{ for all } a_i\in A_i.$$

* An alternative forumlation
	* For any $a_{-i}\in A_{-i}$, the __best-response function__ of player $i$, 

	$$B_i(a_{-i})=\{a_i\in A_i : (a_{-i}, a_i) \ssss_i (a_{-i},a_i^\prime) \text{ for all } a_i^\prime\in A_i\}$$

	* A Nash equilibrium is a profile $a^* $ of action for which
	
	$$a^* _i\in B_i(a^* _{-i}) \text{ for all } i \in N$$

* A possible method of finding Nash equilibria: first calculate the best response function of each player, then find a profile $a^* $ of actions for which $a_i^* \in B_i(a_{-i}^* )$ for all $i\in N$ by solving $\mid N\mid$ equations in $\mid N\mid$ unknowns.

#### 2.3 Examples

(EXAMPLE 15.3) Bach or Stravinsky? (BoS) Two people wish to go out together to a concert of music by either Bach or Stravinsky. Their main concern is to go out together, but one person prefers Bach and the other person prefers Stravinsky. Representing the individuals' preferences by payoff functions, we have 
![fx]({{ '/assets/images/unlisted/bach-or-stravinsky.png' | relative_url }}){: style="width: 50%;" class="center"}

* BoS models a situation in which players wish to coordinate their behavior, but have conflicting interests.
* Two Nash equilibria: (Bach, Bach), (Stravinsky, Stravinsky)

(EXAMPLE 16.1) Two people wish to go out together, but in this case, they agree on the more desirable convert.
![fx]({{ '/assets/images/unlisted/mozart-or-mahler.png' | relative_url }}){: style="width: 40%;" class="center"}

* Nash equilibria: (Mozart, Mozart), (Mahler, Mahler)
* The notion of Nash equilibrium does not rule out a steady state in which the outcome is the inferior equilibrium.

(EXAMPLE 16.2) The Prisoner's Dilemma. Two suspects. If both confess, each will be sentenced to three years in prison. If only one confesses, he will be freed and the other will receive a sentence of four years. If neither confesses, they will both be sentenced to one year in prison.

![fx]({{ '/assets/images/unlisted/prisoners-dilemma.png' | relative_url }}){: style="width: 50%;" class="center"}
* The best outcome for the players is that neither confesses. ??? 
* Whatever one player does, the other prefers Confess to Don’t Confess, so that the game has a unique Nash equilibrium (Confess,Confess). ???

(EXAMPLE 16.3) Hawk-Dove. Two animals are fighting over some prey. Each can  behave like a dove or like a hawk.
![fx]({{ '/assets/images/unlisted/hawk-dove.png' | relative_url }}){: style="width: 30%;" class="center"}
* Equilibria: (Dove, Hawk), (Hawk, Dove)
* Correspond to two different conventions about the player who yields.

(EXAMPLE 17.1) Matching Pennies. 
![fx]({{ '/assets/images/unlisted/matching-pennies.png' | relative_url }}){: style="width: 30%;" class="center"}
* Such a game, in which the interests of the players are diametrically opposed -- "strictly competitive"
* No Nash equilibrium.