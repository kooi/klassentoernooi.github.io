---
type: page
title: Sponsors
permalink: /sponsors/
---

<p>
    Graag wil de organisatie van het klassentoernooi op het barlaeus de volgende sponsors bedanken:
</p>

{% for hash in site.data.sponsors %}
<h2>{{ hash[1].naam }}: </h2>
<img src="{{ hash[1].logo }}">
{% endfor %}
