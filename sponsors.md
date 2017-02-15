---
type: page
title: Sponsors
permalink: /sponsors/
---

<p>
    Graag wil de organisatie van het klassentoernooi op het barlaeus de volgende sponsors bedanken:
</p>

{% for hash in site.data.sponsors %}
{{ hash[1].naam }}: <br/>
<img src="{{ site.url }}/{{ hash[1].logo }}"> <br/>
{% endfor %}
