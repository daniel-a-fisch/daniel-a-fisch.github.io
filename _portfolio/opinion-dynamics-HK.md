---
title: "Predicting Opinion Phases in the Hegselmann-Krause Model"
excerpt: "A short description of my Part III essay about opinion dynamics as part of my MASt in Applied Mathematics at the University of Cambridge.<br/><img src='/files/opinion-dynamics_HK.png' height='300'>"
collection: portfolio
---

In simple terms, the research field of opinion dynamics asks: Given an initial opinion state $x(0)$ and dynamics specified by a set of (general) interaction rules on a network, what can be said about the final behavior of the opinion profile, i.e. $\lim\limits_{t \to \infty} x(t)$? In particular, when is *consensus* $c$ reached, i.e. $\forall i = 1,\dots,N$: $\lim\limits_{t \to \infty} x_i(t) \equiv c$?

In order to address the diversity of the research area of opinion dynamics, I gave a general overview of different types of models for the description of opinion dynamics with focus on the voter, DeGroot and Hegselmann-Krause (HK) model. I also reviewed other models from the literature. 
In addition, I used two simple examples to illustrate the extra effort involved in sequential updating due to randomness, and looked at the network structure that is so central for simultaneous updating.

I then delved deeper into the non-linear HK bounded confidence model with the three opinion phases: consensus, polarization and fragmentation. We are able to gain some fundamental insights using analytical methods, yet other phenomena are better investigated using computer simulations.
The HK model operates according to the principle that dense regions have a stronger influence on less dense ones in their vicinity as seen in the polarized phase, i.e. a (local) majority shapes opinion formation, which makes intuitively sense. 
Using stability analysis, we understand the number of different clusters emerging from the HK model in the fragmented phase better and improved the theoretical estimate for the number of clusters from $\frac{1}{\varepsilon} \rightarrow \frac{1}{2\varepsilon}$ which is much closer to simulation results.
I also looked at alterations of the original model. Introducing a small noise led to quasi-consensus after long enough times. However, a too large noise renders quasi-consensus impossible since opinion clusters can split off and (at least temporarily) continue to evolve independently.
