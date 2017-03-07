---
title: Sponsors
permalink: "/sponsors/"
type: page
sponsors:
- naam: AA Drink
  logo: "/assets/sponsor-logos/aa-drink.gif"
  link: http://aa-drink.com/
- naam: Over
  logo: "/assets/sponsor-logos/over.jpg"
  link: http://over-huiswerkbegeleiding.nl/
- naam: Ooijevaar
  logo: "/assets/sponsor-logos/ooijevaar.gif"
- naam: Sibel
  logo: "/assets/sponsor-logos/sibel.gif"
  link: http://www.sibel.nl
- naam: Sugarfactory
  logo: "/assets/sponsor-logos/sugarfactory.gif"
  link: https://www.sugarfactory.nl/
- naam: Burgermeester
  logo: "/assets/sponsor-logos/burgermeester.gif"
  link: http://www.burgermeester.eu/
- naam: Boom-chicago
  logo: "/assets/sponsor-logos/boomchicago.gif"
  link: http://www.boomchicago.nl/en/
- naam: Res & Smit
  logo: "/assets/sponsor-logos/resensmit.gif"
  link: http://www.ressmit.nl/
- naam: Het Parool
  logo: "/assets/sponsor-logos/parool.gif"
  link: http://www.parool.nl/
- naam: Nusselein
  logo: "/assets/sponsor-logos/nusselein.gif"
  link: http://www.nusselein.nl
- naam: Lokaliften
  logo: "/assets/sponsor-logos/lokaliften.gif"
  link: http://www.lokaliften.nl/
- naam: HCM support
  logo: "/assets/sponsor-logos/hcmsupport.gif"
  link: http://www.hcmsupport.nl/
- naam: Eilders
  logo: "/uploads/eilders.gif"
  link: http://www.eildersreclame.nl/
- naam: The Future Firm
  logo: "/uploads/thefuturefirm.gif"
  link: http://thefuturefirm.com/
- naam: Swart&co
  logo: "/uploads/swartenco.gif"
  link: http://www.swartenco.nl/
---

<p>
    Graag wil de organisatie van het klassentoernooi op het Barlaeus de volgende sponsors bedanken:
</p>

<div class="kolommen">
{% for sponsor in page.sponsors %}
<div class="blok">
<p>
<h2>{{ sponsor.naam }}:</h2>
<a {% if sponsor.link %}href="{{sponsor.link}}"{% endif %}>
<img width="400px" src="{{ sponsor.logo }}" alt="{{ sponsor.naam }}">
</a>
</p>
</div>
{% endfor %}
</div>
