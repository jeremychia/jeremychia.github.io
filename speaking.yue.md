---
layout: default
title: 演講
nav: true
nav_order: 2
footer: true
description: 關於數據工程、風險管理同公民科技嘅會議演講。
permalink: /speaking.html
lang: yue
---

<section class="container mx-auto px-4 py-16">
  <div class="text-center mb-16">
    <h1 class="text-4xl font-bold mb-4">{{ page.title }}</h1>
    <p class="text-gray-600 text-lg">{{ page.description }}</p>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-16">
    {% for speaking in site.speaking %}
    {% include item_card.html item=speaking %}
    {% endfor %}
  </div>
</section>
