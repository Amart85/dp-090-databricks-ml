---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# Azure Databricks Machine Learning ILT Labs

These exercises support Microsoft course [DP-090: Implementing a Machine Learning Solution with Microsoft Azure Databricks](https://docs.microsoft.com/training/courses/dp-090t00) and the associated [Microsoft Learn training content](https://docs.microsoft.com/training/paths/build-operate-machine-learning-solutions-azure-databricks/).

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| Module | Lab |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

## Exercises to support Microsoft Learn modules

{% assign exercises = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %}
{% for activity in exercises  %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
