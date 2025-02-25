---
layout: page
title: Projects
permalink: /projects/
---

#### Basketball Tactical Analysis Dashboard

{% include project-item.html 
content=
"An [interactive dashboard](http://b11-tactical-insights-basketball.course-xai-iml24.isginf.ch/){:target=\"_blank\"} that allows coaches to perform what-if analyses on various tactical game situations. The ML model was trained on real-world basketball game data to predict winning probabilities and generate counterfactual explanations based on team tactical statistics. "
img="../assets/images/projects/b11-dashboard-image-predict.png" %}

#### Backdoor Attack against BIRD in Deep RL

{% include project-item.html 
content=
"Proposed a novel technique to break down the defence of [BIRD](https://proceedings.neurips.cc/paper_files/paper/2023/hash/802e90325f4c8546e13e5763b2ecab88-Abstract-Conference.html){:target=\"_blank\"} against backdoor RL agents. Compared its effectiveness against the vanilla perturbation-based attack [TrojDRL](https://arxiv.org/abs/1903.06638){:target=\"_blank\"}."

img="../assets/images/projects/forl-breakout-attack.gif" %} 


#### Minimax with Alpha-Beta Pruning for Connect 4

{% include project-item.html 
content=
"Python implementation of a Connect 4 AI agent using alpha-beta pruning. 

[[GitHub](https://github.com/hughiemak/alphabeta-connect4){:target=\"_blank\"}]" 

img="../assets/images/projects/connect4.gif" %} 

#### Deep Q-Learning in Cooperative Multi-Agent Reinforcement Learning

{% include project-item.html 
content=
"A personal project in which I implemented the predator prey environment and independent DQNs to solve it. The predator prey environment is a sparse reward problem in which multiple agents have to capture a randomly moving prey by surrounding it in a toroidal gridworld. 

[[GitHub](https://github.com/hughiemak/predator-prey){:target=\"_blank\"}] (contains learning curves and trained models)" 

img="../assets/images/projects/5x5-visualization-cropped.gif" %} 

<!-- <div class="project-item-container">
<div style="float: left; width: 20%;">
<img class="project-item-img" src="../assets/images/projects/5x5-visualization-cropped.gif">
</div>
<div class="project-item-text-container">
<div class="project-item-text">
A personal project in which I implemented the predator prey environment and independent DQNs to solve it. The predator prey environment is a sparse reward problem in which multiple agents have to capture a randomly moving prey by surrounding it in a toroidal grid world. 

[[Code](https://github.com/hughiemak/predator-prey){:target="_blank"}]
</div></div></div> -->

#### Solving Chomp with Policy Iteration

<!-- A personal project in which I applied policy iteration to recover the nontrivial winning strategy of the first player in [Chomp](https://www.math.ucla.edu/~tom/Games/chomp.html){:target="_blank"} via self-play.

[[Report](https://gist.github.com/hughiemak/58bca80976cc3c7dc1dbbafce6fed0f6){:target="_blank"}] [[Code](https://github.com/hughiemak/chomp){:target="_blank"}] -->

{% include project-item.html 
content=
"In the game of [Chomp](https://www.math.ucla.edu/~tom/Games/chomp.html){:target=\"_blank\"}, it can be proven that the first player has a winning strategy without finding out such a strategy. In fact, the strategy is not trivial at all. This motivated the idea of searching for a winning strategy using RL. I defined an environment that simulates the game, then applied policy iteration to extract an optimal strategy for the first player via self-play.

[[Report](https://gist.github.com/hughiemak/58bca80976cc3c7dc1dbbafce6fed0f6){:target=\"_blank\"}] [[GitHub](https://github.com/hughiemak/chomp){:target=\"_blank\"}]"  

img="../assets/images/projects/chomp3.png" %}

<!-- A personal project in which I applied policy iteration to recover the nontrivial winning strategy of the first player in [Chomp](https://www.math.ucla.edu/~tom/Games/chomp.html){:target=\"_blank\"} via self-play. -->


#### Low-Resource NMT System for Chinese-to-Cantonese Translation

{% include project-item.html 
content=
"A summer research internship in which I studied NMT architectures, collected parallel text resources, and trained a Transformer for translating text from the written language (Chinese) to the spoken language (Cantonese) in Hong Kong. 

Parallel text resources in Chinese and Cantonese are scarce. In addition to collecting data from existing studies, I explored the possibility to mine pairs of semantically similar sentences from parallel articles on Chinese and Cantonese Wikipedia and showed that including these sentence pairs in training improves translation performance.

[[Paper](https://dl.acm.org/doi/10.1145/3508230.3508242){:target=\"_blank\"}]
[[Best Presentation Award](https://drive.google.com/file/d/1O9eJjNXD6tir6wfRHPwHXelqK8zHSXoW/view?usp=sharing){:target=\"_blank\"}]"  

img="../assets/images/projects/nmt3.png" %}

<!-- A summer research internship in which I trained a Transformer for translating text from the written language (Chinese) to the spoken language (Cantonese) in Hong Kong. 

Parallel text resources in Chinese and Cantonese are scarce. In addition to collecting data from existing studies, I explored the possibility to increase the amount of training data by mining semantically similar sentences from parallel articles on Chinese and Cantonese Wikipedia. -->

#### Visualizing Linear and Logistic Regression

Interactive visualization of linear regression and logistic regression (motivated by tutorials from YouTube channel *The Coding Train*).

{% include project-item.html 
content="Linear Regression

[[App](https://hughiemak.github.io/VisualizeLinearRegression/){:target=\"_blank\"}] [[GitHub](https://github.com/hughiemak/VisualizeLinearRegression){:target=\"_blank\"}]"
img="../assets/images/projects/linear-regression.png" %}

<!-- Linear Regression: [[App](https://hughiemak.github.io/VisualizeLinearRegression/){:target="_blank"}] [[Code](https://github.com/hughiemak/VisualizeLinearRegression){:target="_blank"}] -->

{% include project-item.html 
content="Logistic Regression

[[App](https://hughiemak.github.io/VisualizeLogisticRegression/){:target=\"_blank\"}] [[GitHub](https://github.com/hughiemak/VisualizeLogisticRegression){:target=\"_blank\"}]"
img="../assets/images/projects/logistic-regression.png" %}

<!-- Logistic Regression: [[App](https://hughiemak.github.io/VisualizeLogisticRegression/){:target="_blank"}] [[Code](https://github.com/hughiemak/VisualizeLogisticRegression){:target="_blank"}] -->

#### Real-Time Reversi Web App

{% include project-item.html
content="A web app for playing Reversi built with Socket.IO. Players can create rooms/join rooms and play with others in real time over the internet. They can also chat with others and create accounts to view their game statistics.

[[App](https://hughiemak.github.io/reversi/){:target=\"_blank\"}] [[Frontend Code](https://github.com/hughiemak/reversi){:target=\"_blank\"}] [[Server Code](https://github.com/hughiemak/reversi-socket-io-server){:target=\"_blank\"}] [[Auth Server Code](https://github.com/hughiemak/reversi-auth){:target=\"_blank\"}]"
img="../assets/images/projects/reversi-play.png" %}

#### Xiang Qi Simulator
{% include project-item.html
content="Xiang Qi (the Chinese chess) is a popular board game in Asia. This is a simple web simulator for Xiang Qi.

[[App](https://hughiemak.github.io/xiangqi/){:target=\"_blank\"}] [[GitHub](https://github.com/hughiemak/xiangqi){:target=\"_blank\"}]"
img="../assets/images/projects/xiangqi.png" %}
