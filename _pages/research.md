---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
redirect_from:
  - /publications/
  - /publications.html
---

{% include base_path %}

My research combines economic modelling with methods from the physics of complex
systems, focusing on how individual interactions aggregate into macroeconomic
outcomes. I work on network economics, labour economics, and heterogeneous-agent
macroeconomics.

{% if site.author.googlescholar %}
  <p>You can also find my articles on <a href="{{ site.author.googlescholar }}">my Google Scholar profile</a>.</p>
{% endif %}

{% assign published = site.research | where: "status", "published" | sort: "date" | reverse %}
{% assign working_papers = site.research | where: "status", "working-paper" | sort: "date" | reverse %}
{% assign in_progress = site.research | where: "status", "work-in-progress" | sort: "date" | reverse %}

{% if published.size > 0 %}
  <h2 class="collection__heading">Publications</h2>
  {% for post in published %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}

<h2 class="collection__heading">Working Papers</h2>
{% if working_papers.size > 0 %}
  {% for post in working_papers %}
    {% include archive-single.html %}
  {% endfor %}
{% else %}
  <p class="collection__empty">No working papers are publicly available yet.</p>
{% endif %}

<h2 class="collection__heading">Work in Progress</h2>
{% if in_progress.size > 0 %}
  {% for post in in_progress %}
    {% include archive-single.html %}
  {% endfor %}
{% else %}
  <p class="collection__empty">Nothing listed here yet.</p>
{% endif %}

<p class="collection__note">
  For research completed before starting the PhD, see
  <a href="{{ base_path }}/projects/">Projects</a>.
</p>
