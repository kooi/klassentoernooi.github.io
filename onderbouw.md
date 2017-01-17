---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
Totaal: 
{% assign totalePunten = '' %}
{% assign puntenLijst = ('' | split: '|') %}
{% for klassennaam in site.data.onderbouw_klassen %}
{% assign punten = 0 %}
{% assign puntenLengte = 0 %} 
  {% for hash in site.data.onderbouw %}
  {% assign onderdeelpunten = 0 %}
  {% assign onderdeel = hash[1] %}
  {% unless onderdeel.geheim %}
    {% for klas in onderdeel.resultaten %}
	  {% if klas.klas == klassennaam %}
        {% assign onderdeelPunten = (klas.punten | times: onderdeel.weging) %}
        {% assign punten = (punten | plus: onderdeelPunten ) %}
      {% endif %}
    {% endfor %}
	{% endunless %}
  {% endfor %}
  {% assign punten = (punten | prepend: "00000" | split: "" | reverse %}
  {% assign punten = (punten | join: "" | truncate: 4, "" | split: "" | reverse | join: "") %}
  {% assign totalePunten = (totalePunten | append: punten | append: ":" | append: klassennaam | append: "|") %} 
{% endfor %}
{% assign totalePunten = (totalePunten | split: "|" | sort | reverse) %}

<ul>
{% for klas in totalePunten %}
  {% assign klasArray = (klas | split: ':' ) %}
  {% assign klassenPunten = (klasArray[0]) %}
  {% assign klassenPuntenArray = (klassenPunten| split: "") %}
  {% assign klassenNaam = klasArray[1] %}
  {% for number in klassenPuntenArray %}
    {% if number == "0" %}
	  {% assign klassenPunten = (klassenPunten | remove_first: "0") %}
	{% else %}
	  {% break %}
	{% endif %}
  {% endfor %}
  <li> {{ forloop.index }}. {{ klassenNaam }} - {{ klassenPunten }} punten </li>
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
