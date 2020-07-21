---
title: Online gehostete Anweisungen
permalink: index.html
layout: home
---

# Inhaltsverzeichnis

Hyperlinks zu den einzelnen exemplarischen Vorgehensweisen. Die Kursleiter können die exemplarische Vorgehensweise als Demonstration oder als Kursteilnehmer-Lab verwenden. 

## Exemplarische Vorgehensweisen

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Modul | Exemplarische Vorgehensweise |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

