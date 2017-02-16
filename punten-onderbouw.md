---
layout: page
title: Punten onderbouw
permalink: /onderbouw/
---
Totaal:
{% assign totalePunten = '' %}
{% assign puntenLijst = ('' | split: '|') %}
{% assign aantalKlassen = (site.data.onderbouw.klassen | size ) %}

{% for klassennaam in site.data.onderbouw.klassen %}
  {% assign punten = 0 %}
  {% assign puntenLengte = 0 %}

  {% for hash in site.data.onderbouw.resultaten %}
  {% assign onderdeelpunten = 0 %}
  {% assign onderdeel = hash[1] %}
  {% unless onderdeel.geheim %}
  {% if onderdeel.resultaten[0].punten %}
    {% for klas in onderdeel.resultaten %}
	  {% if klas.klas == klassennaam %}
        {% assign onderdeelPunten = (klas.punten | times: onderdeel.weging) %}
        {% assign punten = (punten | plus: onderdeelPunten ) %}
      {% endif %}
    {% endfor %}
  {% else %}
    {% assign klassenArray = "" | split: "" %}
    {% for klas in onderdeel.resultaten %}
      {% assign juries = (klas.jury | sort) %}
      {% assign juries = (juries | pop | pop | reverse | pop | pop | reverse) %}
      {% assign aantalJuries = (juries | size) %}
      {% assign jurypunten=0.0 %}

      {% for jury in juries %}
        {% assign jurypunten = (jurypunten | plus: jury) %}
      {% endfor %}

      {% assign jurypunten = (jurypunten | divided_by: aantalJuries | prepend: "") %}
      {% assign jurypunten = (jurypunten | prepend: "00000" | split: "" | reverse %}
      {% assign jurypunten = (jurypunten | join: "" | truncate: 4, "" | split: "" | reverse | join: "") %}
      {% assign klassenPunten = (jurypunten | append: ":" | append: klas.klas) %}
      {% assign klassenArray = (klassenArray | push: klassenPunten) %}

    {% endfor %}
    {% assign klassenArray = (klassenArray | sort | reverse ) %}
    {% assign herhaling = 0 %}
    {% for klasString in klassenArray %}
      {% assign klasArray = (klasString | split: ":") %}

      {% assign vorigeScore = score %}
      {% assign score = klasArray[0] %}
      {% if score == vorigeScore %}
        {% capture herhaling %}{{ herhaling | plus: 1 }}{% endcapture %}
      {% else %}
        {% assign herhaling = 0 %}
      {% endif %}

      {% if klassennaam == klasArray[1] %}
         {% assign onderdeelPunten = (aantalKlassen | minus: forloop.index0 | plus: herhaling | times: onderdeel.weging) %}
         {% assign punten = (punten | plus: onderdeelPunten ) %}
      {% endif %}
    {% endfor %}
    {% endif %}
	{% endunless %}
  {% endfor %}

  {% for klas in site.data.onderbouw.strafpunten %}
      {% if klas.klas == klassennaam %}
        {% assign punten = (punten | minus: klas.strafpunten) %}
      {% endif %}
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

Strafpunten:
{% for klas in site.data.onderbouw.strafpunten %}
  * {{ klas.klas }}: {{ klas.strafpunten }} strafpunten - {{ klas.reden }}
{% endfor %}

{% for hash in site.data.onderbouw.resultaten %}
  {% assign onderdeel = hash[1] %}
  {% unless onderdeel.geheim %}

  {{ hash[0] | capitalize | replace: "_"," "}} (weging: {{ onderdeel.weging }}x)
  {% assign aantalKlassen = (onderdeel.resultaten | size) %}

  {% if onderdeel.resultaten[0].punten %}
  {% assign resultaten = (onderdeel.resultaten | sort: 'punten' | reverse) %}

  <ul>
  {% for klas in resultaten %}

      {% assign punten = (klas.punten | times: onderdeel.weging) %}
      <li> {{ forloop.index }}. {{ klas.klas }} - {{ punten }} punten </li>
  {% endfor %}
  </ul>

  {% else %}
    {% assign klassenArray = "" | split: "" %}
    {% for klas in onderdeel.resultaten %}
      {% assign juries = (klas.jury | sort) %}
      {% assign juries = (juries | pop | pop | reverse | pop | pop | reverse) %}
      {% assign aantalJuries = (juries | size) %}
      {% assign jurypunten=0.0 %}

      {% for jury in juries %}
        {% assign jurypunten = (jurypunten | plus: jury) %}
      {% endfor %}

      {% assign jurypunten = (jurypunten | divided_by: aantalJuries | prepend: "") %}
      {% assign jurypunten = (jurypunten | prepend: "00000" | split: "" | reverse %}
      {% assign jurypunten = (jurypunten | join: "" | truncate: 4, "" | split: "" | reverse | join: "") %}
      {% assign klassenPunten = (jurypunten | append: ":" | append: klas.klas) %}
      {% assign klassenArray = (klassenArray | push: klassenPunten) %}
    {% endfor %}
    {% assign klassenArray = (klassenArray | sort | reverse ) %}
<ul>

    {% for klasString in klassenArray %}
      {% assign klasArray = (klasString | split: ":") %}
      {% assign score = klasArray[0] %}
      {% if score == vorigeScore %}
        {% capture herhaling %}{{herhaling | plus: 1 }}{% endcapture %}
      {% else %}
        {% assign herhaling = 0 %}
      {% endif %}

      {% assign punten = (aantalKlassen | minus: forloop.index0 | plus: herhaling | times: onderdeel.weging) %}
<li>{{ forloop.index | minus: herhaling }}. {{ klasArray[1] }} - {{ punten }} punten </li>
      {% assign vorigeScore = score %}
    {% endfor %}
</ul>

  {% endif %}

  {% endunless %}
{% endfor %}
