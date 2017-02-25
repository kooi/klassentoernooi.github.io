---
layout: page
title: Onderdelen
permalink: /onderdelen/
---
{% assign onderdelen = (site.data.onderdelen | sort) %}
<div class="kolommen">
{% for hash in onderdelen %}
  <div class="blok">
  <h2>{{ hash[1].onderdeel | capitalize }}:</h2>
  <p> {{ hash[1].tekst }} </p>
  </div>
{% endfor %}
</div>
