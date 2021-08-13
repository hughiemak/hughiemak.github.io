---
layout: post
title:  "Finite Markov Decision Processes"
date:   2021-01-17 00:01
---
### 3.1 The Agent-Environment Interface 
* MDPs: straightforward framing of the problem of learning from interaction to achieve a goal 
$
\newcommand{\S}{\mathcal{S}}
\newcommand{\A}{\mathcal{A}}
\newcommand{\R}{\mathcal{R}}
\newcommand{\E}{\mathrm{E}}
\newcommand{\deq}{\dot{=}}
\newcommand{\argmax}{\text{argmax }}
\newcommand{\eps}{\varepsilon}
$
* Agent: learner/decision maker
* Environment: everything outside the agent
![]({{ '/assets/images/unlisted/agent-action-diagram.png' | relative_url }}){: style="width: 75%;" class="center"}
* Agent and environment interact at each time step $t$.
* At each time step t, the agent receives some representation of the environment's state, $S_t\in \S$
and on that basis selects an action, $A_t\in \A(s)$
* One time step later, in part as a consequence of its action, the agent receives a numerical reward, $R_{t+1}\in \R$, and finds itself in a new state, $S_{t+1}$
* Sequence or __trajectory__: $S_0, A_0, R_1, S_2, A_2, R_2, ...$
* In a finite MDP, all sets of states, actions, and rewards all have a finite number of elements
* Random variables $R_t, S_t$ have well defined discrete probability distribution dependent only on the preceding state $S_{t-1}$ and action $A_{t-1}$

$$p(s', r\mid s,a) = Pr(S_t=s', R_t=r \mid S_{t-1}=s, A_{t-1}=a)$$

* The function $p$ defines the __dynamics__ of the MDP. A function of four arguments.
* By the axioms of probability,

$$\sum_{s' \in \S} \sum_{r\in \R} p(s', r\mid s, a)=1, \text{ for all } s\in \S, a\in \A$$

* A state is said to have __the Markov property__ if it includes information about all aspects of the past agent-environment interaction that make a difference for the future.
* State-transition probabilities

$$p(s'\mid s,a)=Pr(S_t=s \mid S_{t-1}=s, A_{t-1}=a)=\sum_r p(s',r\mid s,a)$$

* Expected rewards for state-action pairs

$$r(s,a)=\E[R_t\mid S_{t-1}=s, A_{t-1}=a]=\sum_{r\in \R} r\sum_{s'} p(s',r\mid s,a)$$

* Expected rewards for state-action-next-state 

$$r(s,a,s')=\E[R_t\mid S_{t-1}, A_{t-1}=a, S_t=s']=\sum_{r\in \R} r \frac{p(s', r\mid s,a)}{p(s'\mid s,a)}$$

* The general rule is that anything that cannot be changed arbitrary by the agent considered to be part of the environment
* The agent-evironment boundary represents the limit of the agent's absolute control, not of its knowledge
* __Actions__ represent the possible choices that can be made by the agent
* __States__ represent the basis on which the choices are made
* __Rewards__ define the agent's goal

### 3.2 Goals and Rewards

* At each time step, the reward is a simple number $R_t \in \R$
* The agent's goal is to maximize the total amount of reward it receives - the cumulative reward in the long run.
<div class="box">
*That all of what we mean by goals and purposes can be well thought of as the maximization of the expected value of the cumulative sum of a received scalar signal (called reward). (p.53)* 
</div>
* The agent always learns to maximize its reward. If we want it to do something for us, we must provide rewards to it in such a way that in maximizing them the agent will also achieve out goals.
* The reward signal is your way of communicating to the robot what you want it to achieve, not how you want it achieved.

### 3.3 Returns and Episodes
* Sequence of rewards received after time step $t$: $R_{t+1}, R_{t+2},...$
* Maximize the __expected return__ $G_t=R_{t+1}+R_{t+2}+...+R_T$
* __Episodes__: subsequences of agent-environment interaction
* __Terminal state__: the state in which an episode ends
* __Episodic tasks__: tasks with episodes
* $\S$: the set of all nonterminal states
* $\S^+$: the set of all states plus the terminal state
* $T$: time of termination, a random variable varies from episode to episode
* __Continuing tasks__: Tasks in which the agent-environment interaction goes on continually without limit
<!-- * $T\rightarrow \infty, G_t\rightarrow \infty$ for continuing tasks. -->
* __Discounting__: the sum of the discounted rewards it receives over the future is maximized
* __Expected discounted return__

$$G_t=R_{t+1}+\gamma R_{t+2}+\gamma^2 R_{t+3}+...=\sum_{k=0}^{\infty}\gamma^k R_{t+k+1}$$

* $\gamma$ is called the __discount rate__
* If $\gamma<1$, the infinite sum has a finite value as long as the reward sequence $${R_k}$$ is bounded.
* If $\gamma=0$, the agent is myopic in being concerned only with maximizing immediate rewards
* As $\gamma$ approaches 1, the return object takes future rewards into account more strongly; the agent becomes more farsighted
* Returns at successive time steps

$$G_t=R_{t+1}+\gamma G_{t+1}$$

* Define $G_T=0$

### 3.4 Unified Notation for Episodic and Continuing Tasks
* Consider episode termination to be the entering of a special absorbing state that transitions only to itself and that generates only rewards of zero.
* General notation of expected return

$$G_t=\sum_{k=t+1}^T \gamma^{k-t-1}R_k$$

### 3.5 Policies and Value Functions
* Most RL algorithms involves estimating value functions - functions of states (or of state-action pairs) that estimate how good it is for the agent to be in a given state (or how good it is to perform a given action in a given state)
* The notion of "how good" is defined in terms of expected return
* Expected return depends on what actions the agent will take
* Value functions are defined with respect to particular ways of acting, called __policies__.
* Policy $\pi$: a mapping from states to probabilities of selecting each possible action
* If the agent is following policy $\pi$ at time $t$, $\pi(a\mid s)$ is the probability that $A_t=a$ if $S_t=s$.
* Reinforcement learning methods specify how the agent's policy is changed as a result of its experience.
* __State-value function for policy $\pi$__ (Value function of a state $s$ under a policy $\pi$)

$$v_\pi(s)=\E_\pi[G_t\mid S_t=s]=\E\left[\sum_{k=0}^{\infty} \gamma^k R_{t+k+1}\mid S_t=s\right] $$

* __Action-value function for policy $\pi$__ (Value of taking action $a$ in state $s$ under a policy $\pi$)

$$q_\pi(s, a)=\E_\pi[G_t\mid S_t=s, A_t=a]=\E\left[\sum_{k=0}^{\infty} \gamma^k R_{t+k+1}\mid S_t=s, A_t=a\right] $$

* __$v_\pi$ in terms of $q_\pi$__

$$\begin{align}
v_\pi(s) &= \E[q_\pi(s, A_t)]\\
&= \sum_a \pi(a\mid s)q_\pi(s,a)
\end{align}$$

<div class="box">
The value of a state depends on the values of the actions possible in that state and on how likely each action is to be taken under the current policy. 
![]({{ '/assets/images/unlisted/v-in-terms-of-q.png' | relative_url }}){: style="width: 70%;" class="center"}
</div>

* __$q_\pi$ in terms of $v_\pi$__

$$\begin{align}
q_\pi(s,a)&=\E[R_{t+1} + \gamma v_\pi(S_{t+1}) \mid S_t=s, A_t=a]\\
&=\sum_{s',r} p(s',r\mid s,a)(r+\gamma v_\pi(s'))
\end{align}$$

<div class="box">
The value of an action depends on the next reward, the values of the possible next states and on how likely it is to transition into each next state.
![]({{ '/assets/images/unlisted/q-in-terms-of-v.png' | relative_url }}){: style="width: 55%;" class="center"}
</div>

* __Bellman equation for $v_\pi$__: for any policy and state, the following consistency condition holds between the value of $s$ and the value of its possible successor states $s'$

$$\begin{align}
v_\pi(s)&=\E_\pi [R_{t+1}+\gamma G_{t+1}\mid S_t=s] \\
&=\E_\pi [R_{t+1}+\gamma v_\pi (S_{t+1})\mid S_t=s] \\
&=\sum_a \pi(a\mid s) \sum_{s', r} p(s',r\mid s,a)[r+\gamma v_\pi(s')]
\end{align}$$

* The Bellman equation states that the value of the start state must equal the (discounted) value of the expected next state, plus the reward expected along the way.
* Backup diagram for $v_\pi$
![]({{ '/assets/images/unlisted/backup-diagram-vpi.png' | relative_url }}){: style="width: 30%;" class="center"}
* __Bellman equation for $q_\pi$__

$$\begin{align}
q_\pi(s,a) &= \E_\pi[R_{t+1} + \gamma G_{t+1} \mid S_t=s, A_t=a]\\
&= \E[R_{t+1} + \gamma v_\pi(S_{t+1}) \mid S_t=s, A_t=a]\\
&= \sum_{s',r} p(s',r\mid s,a) \left[r+\gamma\sum_{a'}\pi(a'\mid s')q_\pi(s',a') \right]
\end{align}$$

### 3.6 Optimal Policies and Optimal Value Functions
* A policy $\pi$ is defined to be better than or equal to a policy $\pi'$ if its expected return is greater than or equal to that of $\pi'$ for all states.

$$\begin{align}\pi \geq \pi' \text{ if and only if } v_\pi(s) \geq v_{\pi'}(s) && \text{ for all } s \in \S\end{align}$$

* __Optimal policy $\pi_*$__: There is always at least one policy that is better than or equal to all other policies.
* __Optimal state-value function__

$$\begin{align}v_*(s)=\max_\pi v_\pi(s) \end{align}$$

* __Optimal action-value function__

$$\begin{align}
q_*(s,a) = & \max_\pi q_\pi (s, a) \\
= & \E[R_{t+1}+\gamma v_*(S_{t+1})\mid S_t=s, A_t=a]
\end{align}$$

* Because $v_*$ is the value function for a policy, it must satisfy the self-consistency condition given by the Bellman equation for state values.
* Because it is the optimal value function, it can be written without reference to any specific policy.
* __Bellman optimality equation for $v_*$__

$$\begin{align}
v_*(s)&=\max_{a\in \A(s)} q_{\pi_*} (s,a)\\
& = \max_a \E_{\pi_*}[R_{t+1}+\gamma G_{t+1} \mid S_t=s, A_t=a]\\
& = \max_a \E_{\pi_*}[R_{t+1}+\gamma v_{\pi_*}(S_{t+1}) \mid S_t=s, A_t=a]\\
& = \max_a \sum_{s',r} p(s',r\mid s,a) [r+\gamma v_*(s')]
\end{align}$$

* __Bellman optimality equation for $q_*$__

$$\begin{align}
q_*(s,a) &= \E \left[ R_{t+1}+\gamma \max_{a*} q_*(S_{t+1}, a') \mid S_t=s, A_t=a \right]\\
&= \sum_{s',r} p(s',r\mid s,a) \left[ r + \gamma \max_{a'} q_*(s',a') \right]
\end{align}$$

* For finite MDPs, the Bellman optimality equation for $v_*$ has a unique solution.
* If the dynamic function is given, it is actually a system of equations, one for each state.
* Once we have $v_*$, it is easy to determine an optimal policy: For each state s, there will be one or more actions at which the maximum is obtained in the Bellman optimality equation.

$$\pi_*(s)=\argmax_a \sum_{s'}\sum_{r} p(s',r\mid s,a) [r+\gamma v_*(s')]$$

* Any policy that assigns nonzero probability only to these actions is an optimal policy.
* Any policy that is greedy with respect to the optimal evaluation function $v_*$ is an optimal policy.
* The optimal expected long-term return is turned into a quantity that is locally and immediately available for each state.
* With $q_* $, even easier: for any state $s$, simply choose an action that maximizes $q_* (s,a)$

$$\pi_*(s)=\argmax_a q_*(s,a)$$

* Hence, at the cost of representing a function of state-action pairs, instead of just of states, the optimal action-value function allows optimal actions to be selected without having to know anything about possible successor states and their values, that is, without having to know anything about the environment's dynamics.
* Excplicitly solving the Bellman optimality equation is rarely useful as it assumes
	1. we accurately know the dynamics of the environment. 
	1. we have enough computational resources to complete the computation of the solution. 
	1. the Markov property.
* In RL we typically has to settle for approximate solutions.
* __$v_* $ in terms of $q_* $__

$$\begin{align}
v_*(s) 
&= \sum_a \pi(a\mid s)q_*(s,a)
\end{align}$$

* __$q_* $ in terms of $v_* $__

$$\begin{align}
q_\pi(s,a)
&=\sum_{s',r} p(s',r\mid s,a)(r+\gamma v_*(s'))
\end{align}$$

* Other Bellman equations
![]({{ '/assets/images/unlisted/other-bellman-equations.png' | relative_url }}){: style="width: 60%;" class="center"}

<h3>References</h3>

1. Richard S. Sutton and Andrew G. Barto. Reinforcement Learning: An Introduction; 2nd Edition. 2017.