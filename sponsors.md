---
title: Sponsors
permalink: "/sponsors/"
type: page
---

<p>
    Graag wil de organisatie van het klassentoernooi op het Barlaeus de volgende sponsors bedanken:
</p>

{% for sponsor in site.data.sponsors %}
<p>
<h2>{{ sponsor.naam }}</h2>
<a {% if sponsor.link %}href="{{sponsor.link}}"{% endif %}>
<img width="400px" src="{{ sponsor.logo }}" al>
</a>
<p>
{% endfor %}
