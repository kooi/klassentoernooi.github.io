---
title: Locaties
permalink: "/locaties/"
locaties:
- naam: Vondelpark
  maps: 52.360202,+4.872751
- naam: Melkweg
  maps: Melkweg,Amsterdam+Netherlands
- naam: Olympiaplein
  maps: AVV Swift,Olympiaplein,+Amsterdam
- naam: Barlaeus
  maps: Barlaeus+Gymnasium,Weteringschans,Amsterdam
layout: page
---

<div class="inhoud">
<div class="kopje">Inhoud</div>
<p><a href="#lokalen">Lokalen</a></p>
{% for locatie in page.locaties %}
<p><a href="#{{ locatie.naam }}">{{ locatie.naam | capitalize }}</a></p>
{% endfor %}
</div>

{% for locatie in page.locaties %}
<h3><span id="{{ locatie.naam }}">{{ locatie.naam | capitalize }}:</span></h3>
<iframe height="600px" width="800px" src="https://www.google.com/maps/embed/v1/place?key=AIzaSyBK0TuDzO86O8ZNN-f6-M9So5EE0ZXKJ5g&q={{locatie.maps}}">
</iframe>
{% endfor %}
