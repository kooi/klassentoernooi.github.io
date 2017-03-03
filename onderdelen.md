---
layout: page
title: Onderdelen
permalink: /onderdelen/
---
{% assign onderdelen = (site.data.onderdelen | sort) %}

<div class="inhoud">
<div class="kopje">Inhoud</div>
{% for hash in onderdelen %}
{% assign id= (hash[1].onderdeel | replace: ' ' '_') %}
<p><a href="#{{ id }}">{{ hash[1].onderdeel | capitalize }}</a></p>
{% endfor %}
</div>

<div class="kolommen">
{% for hash in onderdelen %}
  <div class="blok">
  {% assign id= (hash[1].onderdeel | replace: ' ' '_') %}
  <div id="{{ id }}"><h2>{{ hash[1].onderdeel | capitalize }}:</h2></div>
  <p> {{ hash[1].tekst }} </p>
  </div>
{% endfor %}
</div>
