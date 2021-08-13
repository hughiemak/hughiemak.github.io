---
layout: post
title:  "Differential Equations"
date:   2021-01-28 00:01
---
### Separation of Variables

$$\frac{dy}{dt}=ky$$

<div class=box2>

$$\begin{align}
\int \frac{1}{y} \frac{dy}{dt} dt &= \int k dt\\
\ln{\mid y\mid} &= kt+ C\\
y&=\tilde{C}e^{kt}
\end{align}$$

</div>

More generally,

$$\frac{dy}{dt}=f(t)g(y)$$

<div class=box2>

$$\begin{align}
\frac{1}{g(y)}\frac{dy}{dt}&=f(t)\\
\int \frac{1}{g(y)}dy&=\int f(t)dt
\end{align}$$

</div>

Example:

$$\frac{dy}{dx}=\frac{xy}{y^2+1}$$

<div class=box2>

$$\begin{align}
\frac{dy}{dx}&=x \frac{y}{y^2+1}\\
\int \frac{y^2+1}{y} dy&=\int x dx\\
\frac{y^2}{2}+\ln{\mid y\mid}&=\frac{x^2}{2}+C
\end{align}$$

</div>

This is an implicit solution to the differential equation. There is another solution $y=0$ that is not in the form of this implicit equation (a **singular solution**).

### Newton's Law of Cooling

$$\begin{align}
A &= 68^{\circ} F\\
T(0) &= 161^\circ F \\
T(2) &= 153^\circ F
\end{align}$$

<div class=box2>
Modeling using rate of change of temperature

$$\begin{align}
\frac{dT}{dt}&=-k(T-A)\\
\Rightarrow \int \frac{1}{T-A}dT &= \int -k dt \\
\ln(T-A)&= -kt\\
T-A &= e^{-kt}\\
T-A &= De^{-kt}
\end{align}$$

When $t=0$, 

$$161-68 = D = 93$$

When $t=2$, 

$$\begin{align}153.7 - 68 &= 93^{-2k}\\ \Rightarrow k &\approx 0.0409 \end{align}$$

Our model

$$T(t) = 68 + 93e^{-0.0409t}$$

</div>

### Existence and Uniqueness

<div class=box>
#### Theorem

If $f$ and $\frac{\partial{f}}{\partial{y}}$ continuous near $(x_0, y_0)$, then there is a unique solution on an interval $\alpha < x_0< \beta$ to the initial value problem

$$y^\prime=f(x,y), y(x_0)=y_0$$

</div>

<div class="box2">
#### Example

$$y^\prime=y^{1/3}, y(0)=0$$

$y=0$ is a solution.

$$\begin{align}
\int y^{-1/3}dy &= \int dx\\
\frac{3}{2}y^{2/3}&=x+C\\
0&=0+C \Rightarrow C=0\\
\frac{3}{2}y^{2/3}&=x\\
y&=\pm\left(\frac{2}{3}x\right)^{3/2}
\end{align}$$

3 solutions.

</div>
