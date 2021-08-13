---
layout: post
title:  "The Last Marble"
date:   2021-01-13
---

I come across [a video](https://www.youtube.com/watch?v=ZMVkPp_csZ0&ab_channel=%E5%9B%9B%E9%83%8E%E8%AE%B2%E6%A3%8B){:target="_blank"} about an endgame problem in Xiangqi (the Chinese chess). In this problem, there is a winning strategy for the side (red side) that moves first. Lying at the heart of this problem is another problem that can be visualized as a simple marble game. The game starts with two jars of marbles such that at least one jar is non-empty. Two players take turns to pick one of the two jars and draw $n ≥ 1$ marbles from the chosen jar. The one who takes the last marble wins.

It can be proved that the player that makes the first draw will win if and only if the two jars have unequal number of marbles. The following proof is adapted from [an answer to a similar marble problem by user PSPACEhard on Mathematics Stackexchange](https://math.stackexchange.com/questions/1426142/is-there-any-winning-strategy-2015-and-game-with-marbles){:target="_blank"}.

<!-- Let $x_i$ and $y_i$ be the numbers of marbles of the two jars after the $i$-th draw.  -->
Let $x_i$ and $y_i$ be the numbers of marbles of the two jars in the $i$-th turn before the player makes a draw.

<b>Observation 1</b>\\
If $x_i=y_i$, in whatever way the player in the $i$-th turn makes his draw, $x_{i+1}\neq y_{i+1}$.

<b>Observation 2</b>\\
If $x_i\neq y_i$, the player in the $i$-th turn can choose the jar with more marbles and draw enough marbles so that $x_{i+1}=y_{i+1}$.

If $x_i=y_i$, we say that the $i$-th turn is an <b>L-turn</b>. Note that a player cannot draw the last marble in an <b>L-turn</b> because $x_i=y_i\neq 0$ and the player cannot deplete both jars in a single turn.


If $x_i\neq y_i$, we say that the $i$-th turn is a <b>W-turn</b>.

<!-- If $x_i=y_i$, we say that a player is in state $L$ when he is making the $(i+1)$-th draw.

If $x_i\neq y_i$, we say that a player is in state $W$ when he is making the $(i+1)$-th draw. -->

According to the two observations, we have the following conclusions.

- If a player is in an <b>L-turn</b>, the next turn must be a <b>W-turn</b> for his opponent.

- If a player is in an <b>W-turn</b>, the player can always choose the jar with more marbles and draw enough marbles such that the next turn will be a <b>L-turn</b> for his opponent.

If the two jars have the same number of marbles initially, the first turn is an <b>L-turn</b> for the first player. And the next turn will always be a <b>W-turn</b> for the opponent. The opponent can always make a draw such that the first player will continue to be in an <b>L-turn</b>. This cycle repeats until the opponent draws the last marble in a <b>W-turn</b>. 

If the two jars have different number of marbles initially, the first player will be able to draw the last marble by a similar argument.

<!-- - If a player is in state $L$ before the $i$-th draw, then, after the draw, the opponent will be in state $W$.

- If a player is in state $W$ before the $i$-th draw, the player can always choose the jar with more marbles and draw enough marbles such that, after his draw, the opponent will be in state $L$. --> 

<h3>References</h3>
1. [The Xiangqi endgame example by Shiro speaks chess](https://www.youtube.com/watch?v=ZMVkPp_csZ0&ab_channel=%E5%9B%9B%E9%83%8E%E8%AE%B2%E6%A3%8B){:target="_blank"}

1. [A similar marble problem on Mathematics Stackexchange](https://math.stackexchange.com/questions/1426142/is-there-any-winning-strategy-2015-and-game-with-marbles){:target="_blank"}
 