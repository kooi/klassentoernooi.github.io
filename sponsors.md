---
type: page
title: Sponsors
permalink: /sponsors/
---

<p>
    Graag wil de organisatie van het klassentoernooi op het barlaeus de volgende sponsors bedanken:
</p>

{% for hash in site.data.sponsors %}
<div class="kolom">
<h2>{{ hash[1].naam }}: </h2>
<img width="400px" src="{{ hash[1].logo }}">
</div>
{% endfor %}
