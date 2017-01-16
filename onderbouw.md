---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---

{% for hash in site.data.onderbouw %}
{% assign onderdeel = hash[1] %}
  {{ hash[0] | capitalize }} (weging: {{ onderdeel.weging }}x):
  {% for klas in onderdeel.resultaten %}
  <ul>
  <li> {{ klas.klas }} - {{ klas.punten }} </li>
  </ul>
  {% endfor %}
{% endfor %}

