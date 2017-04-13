---
title: Foto's
permalink: "/fotos/"
layout: page
---

<div class="fotos">
{% assign fotos = site.static_files | where: "fotos", true %}
{% for foto in fotos %}
    <div><a href="{{ foto.path }}">
    <img src="{{ foto.path }}" alt="image" />
    </a></div>
{% endfor %}
</div>
