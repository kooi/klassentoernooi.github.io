---
layout: page
title: Locaties
permalink: /locaties/
---
<div class="inhoud">
<div class="kopje">Inhoud</div>
<a href="#{{ locatie.naam }}">{{ locatie.naam | capitalize }}</a>
</div>

{% for locatie in site.data.locaties %}
<div id="locatie.naam"><h3>{{ locatie.naam | capitalize }}:</h3></div>
<iframe height="600px" width="800px" src="https://www.google.com/maps/embed/v1/place?key=AIzaSyBK0TuDzO86O8ZNN-f6-M9So5EE0ZXKJ5g&q={{locatie.maps}}">
{% endfor %}
