---
layout: page
title: research
permalink: /research/
description: Current and ongoing projects. Click a card for details.
nav: true
nav_order: 1
horizontal: false
---

<!-- 这个页面会自动列出 _projects 文件夹里的所有项目，按 importance 从小到大排序。
     新增一个项目 = 在 _projects 里复制一个 .md 文件改内容，不需要改这里。 -->

<div class="projects">
{% assign sorted_projects = site.projects | sort: "importance" %}
{% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
{% else %}
  <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% endif %}
</div>
