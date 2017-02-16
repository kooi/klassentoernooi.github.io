---
layout: page
title: Foto's
permalink: /fotos/
---
<div class="fotos">
{% for image in site.static_files %}
    {% if image.path contains 'fotos' %}
<div><img src="{{ image.path }}" alt="image" /></div>
    {% endif %}
{% endfor %}
</div>
