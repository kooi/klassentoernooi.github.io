---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
Totaal: 
<ul>
{% assign totalePunten = '' %}
{% for klassennaam in site.data.klassen %}
  {% assign punten = 0 %}
  {% assign onderdeelpunten = 0 %}

  {% for hash in site.data.onderbouw %}
    {% assign onderdeel = hash[1] %}
    {% for klas in onderdeel.resultaten %}
	  {% if klas.klas == klassennaam %}
	    {% assign onderdeelpunten = (klas.punten | times: onderdeel.weging) %}
	    {% assign punten = (punten | plus: onderdeelpunten) %}
	  {% endif %}
    {% endfor %}
  {% endfor %}

  {% assign totalePunten = (totalePunten | append: punten) %}
  {% assign totalePunten = (totalePunten | append: ":" %}
  {% assign totalePunten = (totalePunten | append: klassennaam %}
  {% assign totalePunten = (totalePunten | append: '|' %}

{% endfor %}
{% assign totalePunten = (totalePunten | split: '|' ) %}
{% assign totalePunten = (totalePunten | sort | reverse) %}


<ul>
{% for klas in totalePunten %}
  {% assign klassenpunten = (klas | split: ':' %}
  <li> {{ klassenpunten[1] }} - {{ klassenpunten[0] }} </li>
{% endfor %}
</ul>

{% for hash in site.data.onderbouw %}
{% assign onderdeel = hash[1] %}
{% assign resultaten = (onderdeel.resultaten | sort: 'punten' | reverse) %}
  <br>
  {{ hash[0] | capitalize }} (weging: {{ onderdeel.weging }}x):
  {% for klas in resultaten %}
    {% if klas.punten %}
	  {% assign punten = klas.punten %}
	{% endif %}
    <ul>
    <li> {{ klas.klas }} - {{ punten }} </li>
    </ul>
  {% endfor %}
{% endfor %}
