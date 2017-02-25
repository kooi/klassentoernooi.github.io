---
layout: page
title: Foto's
permalink: /fotos/
---
<div class="fotos">
{% for image in site.static_files %}
    {% if image.path contains 'fotos' %}
    <div><a href="{{ image.path }}">
    <img src="{{ image.path }}" alt="image" />
    </a></div>
    {% endif %}
{% endfor %}
</div>
