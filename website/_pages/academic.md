---
layout: page
title: Academic
permalink: /academic/
nav: true
nav_order: 3
description: Research projects and academic work.
---

<div class="projects">
  {% assign academic_projects = site.projects | where: "category", "academic" | sort: "importance" %}
  {% for project in academic_projects %}
    {% include projects.html project=project %}
  {% endfor %}
</div>
