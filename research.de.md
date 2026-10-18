---
layout: default
title: Forschung
nav: true
nav_order: 3
footer: true
description: Akademische Forschung zu Daten, Finanzen und Nachhaltigkeit.
permalink: /research.html
lang: de
---

<section class="container mx-auto px-4 list-page">
  {% include list_header.html %}

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for publication in site.publications %}
    {% include item_card.html item=publication %}
    {% endfor %}
  </div>
</section>
