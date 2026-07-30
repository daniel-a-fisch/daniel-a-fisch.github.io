---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
redirect_from:
  - /portfolio/
  - /portfolio.html
---

{% include base_path %}

Research projects and theses completed before starting the PhD, spanning
opinion dynamics, labour economics, and the physics of complex systems. Current
work is listed under [Research]({{ base_path }}/research/).

{% for post in site.projects %}
  {% include archive-single.html %}
{% endfor %}
