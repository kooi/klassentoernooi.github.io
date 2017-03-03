---
layout: page
title: Onderdelen
permalink: /onderdelen/
---
{% assign onderdelen = (site.data.onderdelen | sort) %}

<div class="inhoud">
<div class="kopje">Inhoud</div>
{% for hash in onderdelen %}
<p><a href='#{{ hash[1].onderdeel | capitalize | replace: " " "_" }}'>{{ hash[1].onderdeel | capitalize }}</a></p>
{% endfor %}
</div>

<div class="kolommen">
{% for hash in onderdelen %}
  <div class="blok">
  <div id='{{ hash[1].onderdeel | capitalize | replace: " " "_" }}'><h2>{{ hash[1].onderdeel | capitalize }}:</h2></div>
  <p> {{ hash[1].tekst }} </p>
  </div>
{% endfor %}
</div>
