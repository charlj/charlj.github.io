---
title: 'Automation, Abundance, and the Struggle for Control'
date: 2026-07-27
permalink: /posts/2026/07/AutomationAbundance/
excerpt: "When produced goods become nearly free, the distributional question collapses onto who controls what stays scarce. Land policy during the transition decides between abundance and domination."
tags:
  - Automation
  - Land
  - Institutions
  - Inequality
---

> **Drafting note.** This essay and model were developed through an iterative human–AI collaboration between the author and ChatGPT. The underlying economic intuition, objections, and direction emerged through the conversation; the mathematical mechanisms and Python implementation were developed and refined jointly. All calibration choices are illustrative rather than empirical estimates.

## 1. The question

The usual fear about automation is that machines will replace workers and leave society with too few jobs. But the limiting case raises a stranger question. Suppose machines eventually become able to reproduce, maintain, power, and improve themselves. Marginal production costs for reproducible goods could then approach zero:

$$
MC_t \rightarrow 0.
$$

With competition,

$$
P_t \rightarrow MC_t \rightarrow 0.
$$

At the same time, if machines can perform essentially every economically useful task,

$$
W_tN_t \rightarrow 0.
$$

The traditional circular flow,

$$
P_tY_t=W_tN_t+R_tK_t+\Pi_t=C_t+I_t+G_t,
$$

then ceases to be the institution that allocates goods. Real output and consumption can remain enormous even while nominal expenditure disappears:

$$
P_t \rightarrow 0,
\qquad
P_tX_t \rightarrow 0,
\qquad
X_t>0.
$$

The final economy therefore separates into two systems:

$$
\boxed{
\begin{aligned}
\text{Reproducible goods} &: \text{automated provisioning or free access},\\
\text{Scarce goods} &: \text{rights, claims, rationing, or political allocation}.
\end{aligned}
}
$$

One qualification matters. Marginal cost falls to zero only for the reproducible bundle. Anything with a non-reproducible input, energy, materials, or land, keeps a price floor equal to the shadow price of that input. Energy is the swing variable. If robots build the solar panels that power the robots, energy joins the free side. If the grid, the sites, and the fuel stay bottlenecks, energy stays a claim to be fought over. How much of output is truly free, and how much remains contested, turns on that one question.

The difficult object is no longer the wage. It is the entitlement vector

$$
\boldsymbol{\omega}_t=(\omega_{1,t},\ldots,\omega_{J,t}),
\qquad
\sum_j\omega_{j,t}=1,
$$

which determines access to land, housing, energy bottlenecks, desirable locations, natural resources, and institutional control.

## 2. The transition is more dangerous than the steady state

Let $a_t\in[0,1]$ denote general automation capability. We use a logistic diffusion path,

$$
a_t=\frac{1}{1+\exp[-\gamma_a(t-\bar t)]}.
$$

Employment changes according to

$$
N_{t+1}-N_t
=
R(a_t)(1-N_t)-D(a_t)N_t,
$$

where displacement rises with automation and opportunities for re-employment decline:

$$
D'(a)>0,
\qquad
R'(a)<0,
\qquad
\lim_{a\to1}R(a)=0.
$$

The last condition is an assumption. It is the pessimistic branch of the task-based view of automation, in which displacement is not offset by the creation of new tasks once machines can perform every task, including the invention of new ones. If some human comparative advantage always survives, wages do not fully collapse. We take the limiting case deliberately.

Temporary automation rents are hump-shaped:

$$
s_t^\Pi=\bar\pi a_t(1-a_t)^\psi.
$$

They first rise because a small number of owners control unusually productive systems. They later fall because machine capital becomes reproducible and its marginal return is competed away. The simulation generates a peak profit share of approximately 0.40 when automation is approximately 0.45.

![Technology transition](/images/Automation/01_technology_transition.png)

This temporary-rent phase may be the decisive historical window. A coalition that understands the transition can exchange rents that will eventually disappear for assets whose political value persists.

## 3. A forward-looking coalition

The coalition receives investable after-tax automation rents

$$
\widetilde\Pi_t
=
(1-\tau_t^\Pi)(1-G_t)s_t^\Pi,
$$

where $G_t$ is the broadly or publicly owned share of productive and scarce assets.

At each date, the coalition chooses a portfolio

$$
\mathbf u_t
=
(u_t^L,u_t^C,u_t^I),
\qquad
u_t^L+u_t^C+u_t^I\leq1,
$$

where:

- $u_t^L$ purchases land and other scarce claims;
- $u_t^C$ builds coercive or physical control capacity;
- $u_t^I$ purchases political, legal, informational, and institutional influence.

For each strategic asset $m\in\lbrace L,C,I\rbrace$, define the coalition's perceived value as a blend of current and discounted future value:

$$
V_t^m
=
(1-\phi)v_t^m
+
\phi
\frac{\sum_{j=1}^H\beta^j v_{t+j}^m}
{\sum_{j=1}^H\beta^j},
$$

where $\phi\in[0,1]$ is foresight. The coalition solves the discrete portfolio problem

$$
\mathbf u_t^*
=
\arg\max_{\mathbf u\in\mathcal U}
\left (
\begin{aligned}
&\widetilde\Pi_t\Big[
\eta_Lu_t^LV_t^L\widetilde\chi_t(1-H_t)
+\eta_Cu_t^CV_t^C(1-C_t)(\alpha_C+H_t)\\
&\qquad\qquad
+\eta_Iu_t^IV_t^I(1-I_t)(\alpha_I+C_t)
\Big]\\
&+\nu\widetilde\Pi_t(1-u_t^L-u_t^C-u_t^I)
-\frac{\kappa_u}{2}\left[(u_t^L)^2+(u_t^C)^2+(u_t^I)^2\right]
\end{aligned}
\right ).
$$

The model does not require every rich household, corporation, or public official to behave this way. It requires only that one sufficiently organized coalition recognizes that temporary rents can be converted into durable control before other groups coordinate.

Foresight on its own does not deliver the capture. If everyone could see the transition coming, the future scarcity value of land would already sit in today's land price, because asset markets price the future. The coalition would then pay full value and gain nothing. The advantage is therefore not foresight. It is asymmetric foresight paired with the cash to act on it. The coalition sees the transition while workers, voters, and public institutions do not, and it alone holds the transitory rents that let it buy while others cannot. Strip out either the asymmetry or the rents, and the capture disappears. This narrows the danger, and it tells us where to intervene: close the information gap, or deny the rents their private use.

The strategic stocks evolve as

$$
H_{t+1}-H_t
=
\eta_Lu_t^L\widetilde\Pi_t(1-H_t)
+\text{ordinary acquisition}_t
-\text{dilution}_t,
$$

$$
C_{t+1}-C_t
=
\eta_Cu_t^C\widetilde\Pi_t(1-C_t)-\delta_CC_t,
$$

and

$$
I_{t+1}-I_t
=
\eta_Iu_t^I\widetilde\Pi_t(1-I_t)-\delta_II_t.
$$

The simulated coalition purchases land early, then shifts toward coercive capacity and influence as the wage-system threshold approaches.

![Forward-looking coalition strategy](/images/Automation/03_forward_coalition_strategy.png)

![Control capital](/images/Automation/04_control_capital.png)

## 4. Legal enforcement is not the same as physical control

Let $\chi_t$ be legitimate legal enforceability. It declines when exclusion becomes extreme. But a powerful coalition may retain physical control even when the legal order loses legitimacy. Define

$$
\widetilde\chi_t
=
\chi_t
+(1-\chi_t)(\bar c+\rho_CC_t),
$$

where $\bar c$ is baseline coercive capacity and $C_t$ is the accumulated strategic stock.

This distinction creates two bad outcomes:

1. **Collapse:** legal enforcement and physical control both fail.
2. **Authoritarian scarcity:** legitimate enforcement fails, but an organized coalition retains control of land, infrastructure, machines, security, and communications.

In the myopic capture simulation, final legitimate enforcement is only 0.07, and the system collapses because durable control was not built. In the forward-looking case, legitimate enforcement is similarly weak at 0.03, but effective control remains 0.65. The outcome is therefore classified as **Authoritarian scarcity** rather than collapse.

![Enforcement and exclusion](/images/Automation/05_enforcement_and_exclusion.png)

## 5. Political power determines the entitlement vector

Public and coalition power are represented by

$$
\mathcal P_t^P
=
\alpha_0^P
+\alpha_LL_t
+\alpha_SS_t
+\alpha_GG_t
+\alpha_x\max(x_t,0),
$$

and

$$
\mathcal P_t^E
=
\alpha_0^E
+\alpha_HH_t
+\alpha_CC_t
+\alpha_II_t
+\alpha_x\max(-x_t,0).
$$

The public entitlement share follows a contest-success function:

$$
\omega_t^P
=
\frac{(\mathcal P_t^P)^\kappa}
{(\mathcal P_t^P)^\kappa+(\mathcal P_t^E)^\kappa}.
$$

This does not assume that formal constitutions are irrelevant. Legitimacy enters public power directly. But constitutions are effective only when enough organizational and material power remains behind them.

## 6. The institutional bifurcation

Let $x_t$ describe the political-economic regime:

$$
x_t>0
\quad\Longrightarrow\quad
\text{inclusive abundance},
$$

$$
x_t<0
\quad\Longrightarrow\quad
\text{exclusionary or coercive allocation}.
$$

Its stochastic dynamics are

$$
dx_t
=
\left[\mu(a_t)x_t-cx_t^3+b_t\right]dt
+\sigma_xdB_t,
$$

with

$$
\mu(a_t)=\kappa_a(a_t-a^*).
$$

Before $a^*$, the wage-based status quo is stable. After $a^*$, the middle becomes unstable and two branches emerge:

$$
x_+^*=+\sqrt{\frac{\mu(a)}{c}},
\qquad
x_-^*=-\sqrt{\frac{\mu(a)}{c}}.
$$

The bias term is endogenous:

$$
b_t
=
b_0
+\beta_SS_t
+\beta_LL_t
+\beta_GG_t
+\beta_\omega\omega_t^P
-\beta_HH_t
-\beta_CC_t
-\beta_II_t
-\beta_EE_t.
$$

The multiplicity here is imposed. The cubic potential is a reduced form for a deeper mechanism: power is self-reinforcing, so control today buys more control tomorrow, and increasing returns of that kind generate more than one resting point. Technology makes the old allocation system unstable. Social solidarity, legitimacy, broad ownership, concentration, coercion, influence, and exclusion then determine which replacement becomes locally attractive.

![Bifurcation diagram](/images/Automation/06_bifurcation_diagram.png)

## 7. Three simulations with the same technology

The technological and employment paths are identical across the scenarios. That identity is the point of the exercise, so it is worth seeing the numbers.

**Common calibration (illustrative, identical in every run).**

| Object | Form or value |
|---|---|
| Automation path $a_t$ | logistic, growth $\gamma_a = 0.085$, midpoint $\bar t = 55$ |
| Displacement, re-employment | $D(a)=0.002+0.075\,a^{2.6}$; $R(a)=0.05(1-a)^{2.2}$ |
| Automation profit (raw) | $2.8\,a(1-a)^{1.6}$, peaking near a 0.40 share at $a\approx0.45$ |
| Scarcity rent (raw) | $0.08 + 0.95\,a^{3}$ |
| Regime dynamics | $\mu(a)=0.08(a-0.62)$, cubic coefficient $c=0.08$, noise $\sigma_x=0.02$ |
| Contest elasticity $\kappa$ | 2.5 |
| Horizon, step | $T=120$, $dt=0.1$ |

**The levers that differ.**

| Lever | Institutional adaptation | Myopic capture | Forward coalition |
|---|---:|---:|---:|
| Profit tax $\tau^\Pi$ | 0.45 | 0.08 | 0.08 |
| Land tax | 0.35 | 0.05 | 0.05 |
| Public conversion (to $G$) | 0.30 | 0.03 | 0.03 |
| Redistribution | 0.18 | 0.01 | 0.01 |
| Solidarity $S$ | 0.45 | 0.06 | 0.06 |
| Legitimacy $\chi$ | 0.40 | 0.08 | 0.08 |
| Coalition foresight $\phi$ | 0.70 | 0.00 | 0.95 |
| Strategic intensity | 0.40 | 0.00 | 1.60 |
| **Outcome** $x^*$ | **+0.76, inclusive** | **Collapse** | **−0.87, authoritarian scarcity** |

The second table is uncomfortable. Nothing about the machines decides the outcome. The tax on transitory profits, the share of assets converted to broad ownership, and how far the coalition looks ahead decide it.

### Institutional adaptation

Temporary rents are partly converted into broad ownership. Public ownership reaches 0.68, elite concentration falls to 0.18, and the institutional state converges to $x=0.76$.

### Myopic power capture

Private owners accumulate scarce assets but do not build enough durable control capacity. Elite concentration reaches 0.98; exclusion approaches 1.00; the legal order fails; and the result is **Collapse**.

### Forward-looking coalition

The coalition anticipates the end of automation rents and builds land ownership, coercive capacity, and political influence. Final coercive capacity is 0.60, influence is 0.59, and the institutional state converges to $x=-0.87$. The result is **Authoritarian scarcity**.

![Institutional paths](/images/Automation/02_institutional_paths.png)

## 8. Stochastic outcomes

The simulations are not forecasts. They demonstrate a mechanism. A preparedness index jointly increases broad ownership, legitimate fiscal capacity, redistribution, solidarity, and institutional resilience while reducing the coalition's available rents.

| Preparedness | Inclusive abundance | Authoritarian scarcity | Collapse |
|---:|---:|---:|---:|
| 0.4 | 0.00 | 0.99 | 0.00 |
| 0.8 | 0.46 | 0.36 | 0.07 |
| 1.0 | 0.97 | 0.00 | 0.01 |

![Monte Carlo preparedness](/images/Automation/07_monte_carlo_preparedness.png)

The relationship is nonlinear. Near the tipping region, apparently modest institutional differences produce large changes in outcome probabilities.

The foresight experiment is equally important. Once the coalition looks sufficiently far ahead to recognize the future value of control, temporary rents are no longer simply consumed. They are converted into assets that survive the disappearance of profits.

![Foresight sweep](/images/Automation/08_foresight_sweep.png)

## 9. Interpretation

Automation itself is not the villain in this model. In the inclusive branch it eliminates drudgery, expands leisure, and makes reproducible goods extraordinarily abundant.

The danger is a mismatch in timing:

$$
\text{technology changes quickly}
\qquad\text{but}
\qquad
\text{entitlement institutions change slowly}.
$$

A forward-looking power-seeking coalition may act before ordinary workers, voters, and institutions understand that the wage system is temporary. Its first-mover advantage is not primarily the permanent ownership of robots. Freely reproducible robots eventually cease to earn rents. The advantage comes from using temporary profits to acquire the scarce and political complements of automation:

$$
\boxed{
\text{land}
+\text{energy and infrastructure}
+\text{coercive capacity}
+\text{political influence}
+\text{control of machine systems}.
}
$$

This makes the transition a constitutional problem rather than merely a labor-market problem.

### Where this sits

The claim that value migrates to non-reproducible factors is old, and it is well supported. When what is produced is cheap, the surplus accrues to what cannot be produced: this is the classical rent argument of Ricardo and of Henry George. The modern evidence points the same way. Rognlie (2015) showed that the rise in capital's share is almost entirely housing and land rather than machines. The task-based view of automation (Acemoglu and Restrepo) supplies the labor-market half: automation displaces workers directly, and only the creation of new tasks offsets it. Our limiting case is the one in which that offset runs out.

### What "manage land well" actually means

If the binding scarcity is land and the other non-reproducible assets, the policy follows from an old and hard result. Land is supplied inelastically. A tax on the rent it earns does not distort its use. Henry George saw this in 1879, and it remains the least-distorting tax in public finance. The same logic governs the automated economy. Tax the rent on the scarce complements, the land, the spectrum, the location, the energy bottleneck, and leave the reproducible sector to fall toward zero cost. The abundance survives the tax, because the tax lands on what cannot flee. The revenue then funds universal access. This is the concrete content of managing land well. It is not the seizure of the robots, which soon earn nothing. It is the socialization of the rent on what stays scarce.

## 10. What the model does not yet contain

Several extensions would materially improve the exercise:

1. Multiple competing coalitions rather than one organized elite.
2. Endogenous collective action by displaced households.
3. Strategic robots or autonomous systems as an independent actor.
4. International mobility of capital, machines, land claims, and coercive capacity.
5. A richer housing and spatial model.
6. Endogenous moral preferences, solidarity, and legitimacy.
7. Explicit debt, pensions, mortgages, and nominal-contract breakdown.

The model's central claim is: **when temporary technological rents can be converted into durable political control, foresight itself becomes a source of power.** Whether automation produces abundance for everyone or abundance under domination depends on what happens during that temporary window.

## 11. The benevolent-trustee equilibrium

There is another possible route to the inclusive branch. A government, wealthy coalition, or other powerful first mover may anticipate that automation will eliminate wages, concentrate scarce assets, and eventually create civil conflict. It could therefore use the temporary profit phase to acquire land, housing, energy systems, and other essential assets before their scarcity value rises further.

But foresight alone is not sufficient. The favorable equilibrium requires

$$
\boxed{
\text{foresight}
+\text{benevolence}
+\text{credible self-restraint}
}.
$$

The coalition must be willing to convert private ownership into a durable system of universal access. For example, essential land and housing could be placed in a social trust with entitlement shares

$$
\omega_{i,t}=\frac{1}{N_t},
\qquad
\sum_{i=1}^{N_t}\omega_{i,t}=1.
$$

The trust could retain legal ownership while households receive permanent, non-revocable use rights:

$$
h_{i,t}=\omega_{i,t}\bar H.
$$

This avoids the need to divide every physical asset while preventing exclusion from essential goods.

The central difficulty is commitment. A benevolent founder may be replaced by less benevolent successors, or the coalition may later prefer control to universal access. The durable distinction is therefore between an allocation determined by a rule,

$$
\omega_{i,t}=\Omega_i(\text{constitutional rule}),
$$

and one determined by the current ruler,

$$
\omega_{i,t}=\Omega_i(\text{discretionary choice}).
$$

The first is potentially self-sustaining; the second depends continuously on the character of whoever holds power. Paradoxically, the most benevolent use of concentrated power may therefore be to create institutions that permanently limit that power. The first mover acquires scarce assets not to remain their ultimate owner, but to act as a trustee for the post-labor economy.

Obviously parts of this analysis sit uncomfortably with me, but I do not see a way out of it yet. I do not like state or communal control of private property. I detest it. However, I think that not everyone thinks that land ownership is important today, or perhaps they do not have the means to obtain land. But if all jobs can be automated away (this has never happened in our history, but history is not a perfect predictor of our future) then the analysis clearly shows that those who own raw materials (or the land) stand to hold power. That power is obviously weak when few have access to food and life-sustaining resources. This can lead to civil unrest where land ownership becomes risky. 
