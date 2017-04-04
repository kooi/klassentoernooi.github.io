---
title: Lokalen
permalink: "/lokalen"
lokalen:
- klas: 1A
  lokaal: 2.7
- klas: 1B
  lokaal: 1.2
- klas: 1C
  lokaal: 0.3
- klas: 1D
  lokaal: 0.6
- klas: 1E
  lokaal: 1.12
- klas: 2A
  lokaal: 1.10
- klas: 2B
  lokaal: 1.4
- klas: 2C
  lokaal: 0.5
- klas: 2D
  lokaal: 0.8
- klas: 2E
  lokaal: 1.6
- klas: 3A
  lokaal: 1.8
- klas: 3B
  lokaal: 2.9
- klas: 3C
  lokaal: 2.3
- klas: 3D
  lokaal: 2.5
- klas: 3E
  lokaal: 2.8
- klas: 4A
  lokaal: 1.11
- klas: 4B
  lokaal: 2.4
- klas: 4C
  lokaal: 1.13
- klas: 4D
  lokaal: 2.2
- klas: 4E
  lokaal: 2.6
- klas: 5A
  lokaal: 2.11
- klas: 5B
  lokaal: 3.2
- klas: 5C
  lokaal: S8
- klas: 5D
  lokaal: S2
- klas: 5E
  lokaal: 1.1
layout: page
---

<div class="lokalen">
<h3><div id="lokalen">Lokalen</div></h3>
<ul>
{% for lokaal in page.lokalen %}
<li>{{ lokaal.klas }} - {{ lokaal.lokaal }}</li>
{% endfor %}
</ul>
</div>
