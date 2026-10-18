---
layout: default
title: Research
nav: true
nav_order: 3
footer: true
description: Peer-reviewed research on data, finance, and sustainability.
---

<section class="container mx-auto px-4 list-page">
  {% include list_header.html %}

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for publication in site.publications %}
    {% include item_card.html item=publication %}
    {% endfor %}
  </div>
</section>
