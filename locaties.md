---
layout: page
title: Locaties
permalink: /locaties/
---
<div class="inhoud">
<div class="kopje">Inhoud</div>
{% for locatie in site.data.locaties %}
<p><a href="#{{ locatie.naam }}">{{ locatie.naam | capitalize }}</a></p>
</div>
{% endfor %}

{% for locatie in site.data.locaties %}
<h3><span id="{{ locatie.naam }}">{{ locatie.naam | capitalize }}:</span></h3>
<iframe height="600px" width="800px" src="https://www.google.com/maps/embed/v1/place?key=AIzaSyBK0TuDzO86O8ZNN-f6-M9So5EE0ZXKJ5g&q={{locatie.maps}}">
{% endfor %}
