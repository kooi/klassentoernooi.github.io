---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
<a> Totaal: 
<ul>
{% assign totalePunten = '' %}
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
  {% assign totalePunten = (totalePunten | append: punten) %}
  {% assign totalePunten = (totalePunten | append: ":" %}
  {% assign totalePunten = (totalePunten | append: klassennaam %}
  {% assign totalePunten = (totalePunten | append: '|' %}
{% endfor %}
{% assign totalePunten = (totalePunten | split: '|' ) %}
{% assign totalePunten = (totalePunten | sort ) %}


<ul>
{% for klas in totalePunten %}
  {% assign klassenpunten = (klas | split: ':' %}
  <li> {{ klassenpunten[1] }} - {{ klassenpunten[0] }} </li>
{% endfor %}
</ul>

{% for hash in site.data.onderbouw %}
{% assign onderdeel = hash[1] %}
  <br>
  {{ hash[0] | capitalize }} (weging: {{ onderdeel.weging }}x):
  {% for klas in onderdeel.resultaten %}
  <ul>
  <li> {{ klas.klas }} - {{ klas.punten }} </li>
  </ul>
  {% endfor %}
{% endfor %}
