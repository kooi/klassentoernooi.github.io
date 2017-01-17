---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
<a> Totaal: 
<ul>
{% for klassennaam in site.data.klassen %}
  {% assign punten = 0 %}
  {% for hash in site.data.onderbouw %}
  {% assign onderdeel = hash[1] %}
    {% for klas in onderdeel.resultaten %}
	{% if klas.klas == klassennaam %}
	  {% assign punten = (punten | plus: (klas.punten | times: onderdeel.weging)) %}
	{% endif %}
	{% endfor %}
  {% endfor %}
  <li>{{ klassennaam }} - {{ punten }}</li>
{% endfor %}
</ul>

{% for hash in site.data.onderbouw %}
{% assign onderdeel = hash[1] %}
  {{ hash[0] | capitalize }} (weging: {{ onderdeel.weging }}x):
  {% for klas in onderdeel.resultaten %}
  <ul>
  <li> {{ klas.klas }} - {{ klas.punten }} </li>
  </ul>
  {% endfor %}
{% endfor %}

