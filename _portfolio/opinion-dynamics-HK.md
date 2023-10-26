---
title: "Predicting Opinion Phases in the Hegselmann-Krause Model"
excerpt: "A short description of my Part III essay about opinion dynamics as part of my MASt in Applied Mathematics at the University of Cambridge.<br/><img src='/files/opinion-dynamics_HK.png' width='40%'>"
collection: portfolio
---

In simple terms, the research field of opinion dynamics asks: Given an initial opinion state $x(0)$ and dynamics specified by a set of (general) interaction rules on a network, what can be said about the final behavior of the opinion profile, i.e. $\lim\limits_{t \to \infty} x(t)$? In particular, when is *consensus* $c$ reached, i.e. $\forall i = 1,\dots,N$: $\lim\limits_{t \to \infty} x_i(t) \equiv c$?

In order to address the diversity of the research area of opinion dynamics, I give a general overview of different types of models for the description of opinion dynamics with focus on the voter, DeGroot and Hegselmann-Krause (HK) model. I also review other models from the literature. 
In addition, I use two simple examples to illustrate the extra effort involved in sequential updating due to randomness, and look at the network structure that is so central for simultaneous updating.

<p float="left">
  <img align="top" src="../../files/HK-consensus.png" width="32%" />
  <img align="top" src="../../files/HK-polarization.png" width="32%" />
  <img align="top" src="../../files/HK-cluster.png" width="32%" /><br/>
  <em>The different opinion phases of the HK model: consensus, polarization and fragmentation.</em>
</p>
I then delve deeper into the non-linear HK bounded confidence model with the three opinion phases: consensus, polarization and fragmentation. We are able to gain some fundamental insights using analytical methods, yet other phenomena are better investigated using computer simulations.
The HK model operates according to the principle that dense regions have a stronger influence on less dense ones in their vicinity as seen in the polarized phase, i.e. a (local) majority shapes opinion formation, which makes intuitively sense. 
Using stability analysis, we understand the number of different clusters emerging from the HK model in the fragmented phase better and improved the theoretical estimate for the number of clusters from $\frac{1}{\varepsilon} \rightarrow \frac{1}{2\varepsilon}$ which is much closer to simulation results.
I also look at alterations of the original model. Introducing a small noise led to quasi-consensus after long enough times. However, a too large noise renders quasi-consensus impossible since opinion clusters can split off and (at least temporarily) continue to evolve independently.
<p float="left">
  <img align="top" src="../../files/opinion-dynamics_HK.png" width="48%" />
  <img align="top" src="../../files/HK-noisy-no-quasi-cons.png" width="48%" /><br/>
  <em>Small noise leads to quasi-consensus. However, large noise leads to temporary cluster formation.</em>
</p>
