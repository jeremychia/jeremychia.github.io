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

<section class="container mx-auto px-4 py-16">
  <div class="text-center mb-16">
    <h1 class="text-4xl font-bold mb-4">{{ page.title }}</h1>
    <p class="text-gray-600 text-lg">{{ page.description }}</p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for publication in site.publications %}
    {% include item_card.html item=publication %}
    {% endfor %}
  </div>
</section>
