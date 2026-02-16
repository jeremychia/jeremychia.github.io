---
layout: default
title: Speaking
nav: true
footer: true
description: Conference talks on data engineering, risk management, and civic tech.
---

<section class="container mx-auto px-4 py-16">
  <div class="text-center mb-16">
    <h1 class="text-4xl font-bold mb-4">{{ page.title }}</h1>
    <p class="text-gray-600 text-lg">{{ page.description }}</p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for speaking in site.speaking %}
    {% include speaking_card.html speaking=speaking %}
    {% endfor %}
  </div>
</section>
