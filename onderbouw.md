---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
Totaal: 
{% assign totalePunten = '' %}
{% for klassennaam in site.data.klassen %}
  {% assign punten = 0 %}

  {% for hash in site.data.onderbouw %}
  {% assign onderdeelpunten = 0 %}
  {% assign onderdeel = hash[1] %}
	{% unless onderdeel.geheim %}
    {% for klas in onderdeel.resultaten %}
	  {% if klas.klas == klassennaam %}
	    {% assign onderdeelpunten = (klas.punten | times: onderdeel.weging) %}
	    {% assign punten = (punten | plus: onderdeelpunten) %}
	  {% endif %}
    {% endfor %}
	{% endunless %}
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
  <li> {{ forloop.index }}. {{ klassenpunten[1] }} - {{ klassenpunten[0] }} punten </li>
{% endfor %}
</ul>

{% for hash in site.data.onderbouw %}
{% assign onderdeel = hash[1] %}
{% unless onderdeel.geheim %}

{{ hash[0] | capitalize }} (weging: {{ onderdeel.weging }}x)
<ul>

{% assign resultaten = (onderdeel.resultaten | sort: 'punten' | reverse) %}
{% for klas in resultaten %}
  {% if klas.punten %}
    {% assign punten = (klas.punten | times: onderdeel.weging) %}
  {% endif %}
  <li> {{ forloop.index }}. {{ klas.klas }} - {{ punten }} punten </li>
{% endfor %}

</ul>
{% endunless %}
{% endfor %}
