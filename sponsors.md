---
title: Sponsors
permalink: "/sponsors/"
type: page
---

<p>
    Graag wil de organisatie van het klassentoernooi op het Barlaeus de volgende sponsors bedanken:
</p>

<div class="kolommen">
{% for sponsor in site.data.sponsors %}
<div class="blok">
<p>
<h2>{{ sponsor.naam }}</h2>
<a {% if sponsor.link %}href="{{sponsor.link}}"{% endif %}>
<img width="400px" src="{{ sponsor.logo }}" alt="{{ sponsor.naam }}">
</a>
</p>
</div>
{% endfor %}
</div>
