---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
<a> Totaal: 
<ul>
{% for klas in site.data.klassen %}
  {% assign punten = 0 %}
  {% for hash in site.data.onderbouw %}
  {% assign onderdeel = hash[1] %}
    {% for klasz in onderdeel.resultaten %}
	{% if klasz.klas == klas %}
	  {% assign punten = (punten | plus: (klasz.punten | times: onderdeel.weging)) %}
	{% endif %}
	{% endfor %}
  {% endfor %}
  <li>{{ klas }} - {{ punten }}</li>
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

