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
  logo: "/uploads/hcmsupport-a146bc.gif"
  link: http://www.hcmsupport.nl/
- naam: Eilders
  logo: "/uploads/eijlders.gif"
  link: https://www.leidseplein.amsterdam/cafe/cafe-eijlders
- naam: The Future Firm
  logo: "/uploads/thefuturefirm.png"
  link: http://thefuturefirm.com/
- naam: Swart&co
  logo: "/uploads/swartenco.gif"
  link: http://www.swartenco.nl/
- naam: FC Hyena
  logo: "/uploads/hyena.gif"
  link: https://fchyena.nl/
- naam: CZAR
  logo: "/uploads/CZAR-NL-2b0a36.gif"
  link: http://czar.nl/
- naam: Café Reynders
  logo: "/uploads/logo.gif"
  link: http://www.cafereynders.nl/#1
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
