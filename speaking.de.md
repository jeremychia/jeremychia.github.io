---
layout: default
title: Vorträge
nav: true
nav_order: 2
footer: true
description: Konferenzvorträge zu Data Engineering, Risikomanagement und Civic Tech.
permalink: /speaking.html
lang: de
---

<section class="container mx-auto px-4 list-page">
  {% include list_header.html %}

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for speaking in site.speaking %}
    {% include item_card.html item=speaking %}
    {% endfor %}
  </div>
</section>
