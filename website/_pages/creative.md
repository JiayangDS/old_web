---
layout: page
title: Creative
permalink: /creative/
nav: true
nav_order: 4
description: >
  Before entering data science, I co-founded a creative-industry startup.
  This page collects projects where technology meets creative storytelling
  and business.
---

<div class="projects">
  {% assign creative_projects = site.projects | where: "category", "creative" | sort: "importance" %}
  {% for project in creative_projects %}
    {% include projects.html project=project %}
  {% endfor %}
</div>
