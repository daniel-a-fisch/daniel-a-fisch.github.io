---
layout: page
permalink: /
hide_title: true
redirect_from:
  - /about/
  - /about.html
---

<div class="intro">
  <div class="intro__text">
    <h1 class="intro__name">Daniel A. Fisch</h1>
    <div class="intro__role">PhD student in Economics, Massachusetts Institute of Technology</div>
  </div>
  <img src="{{ site.author.avatar | relative_url }}" alt="Daniel A. Fisch" class="intro__photo">
</div>

I am a current PhD student in Economics at [MIT](https://economics.mit.edu/people/phd-students/daniel-fisch). Previously, I worked for [QuantCo](https://www.quantco.com/) as a data scientist in London and Munich. I hold master's degrees in both Economics ([BSE](https://www.bse.eu), 2024) and Applied Mathematics ([University of Cambridge](https://www.damtp.cam.ac.uk/), 2023). I graduated from the [University of Göttingen](https://www.uni-goettingen.de/en/20493.html/) with a BSc in Physics in 2022.

**I am an Economist and Theoretical Physicist** who strives to actively contribute to the solution of some of the most relevant societal problems. By providing tools, theories and models to understand the underlying dynamics, I aim to empower society to address the fundamental root causes in an effective and efficient way. More precisely, I intend to achieve this by combining economic modeling and analyses with methods from the physics of complex systems, network dynamics and stochastic processes.

I am intrigued by emergent phenomena and want to **understand how underlying micro-level interactions lead to macro-dynamics and influence aggregate economic outcomes**. In particular, I am interested in questions about how, in network economics, the mechanisms of individual social interactions determine our aggregate behaviour, how in labour economics, by matching workers and employers, wages and unemployment are shaped, and how heterogeneous agents drive macroeconomics.

See my [Research page](/research/) for more details on my work, or an example project [published by UPF](http://hdl.handle.net/10230/68457).

<div class="section">
  <h2 class="section__title">Research interests</h2>
  <ul class="interests">
    {% for item in site.data.interests %}<li>{{ item }}</li>{% endfor %}
  </ul>
</div>

<div class="section">
  <h2 class="section__title">Research</h2>
  {% include research-list.html limit=3 %}
  <p><a href="{{ "/research/" | relative_url }}">All research</a></p>
</div>

<div class="section">
  <h2 class="section__title">Contact</h2>
  {% include contact.html %}
</div>
