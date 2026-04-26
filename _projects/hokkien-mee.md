---
layout: project
title: "Hokkien Mee Map"
image: "/assets/images/projects/hokkien-mee.png"
featured: true
category: Data Product
tags:
  - python
  - playwright
  - nlp
  - mapping
  - singapore
  - hokkien mee
links:
  - title: Live Site
    url: https://jeremychia.github.io/hokkien-mee/
  - title: GitHub
    url: https://github.com/jeremychia/hokkien-mee
---

An end-to-end pipeline that turns posts from the **Hokkien Mee Hunting** Facebook group into an interactive map of stalls across Singapore — with sentiment ratings, food photo classification, and proximity search.

## What it does

- Scrapes public group posts using **Playwright** with human-like scroll behaviour and cookie-based authentication
- Downloads and classifies food photos using a **fine-tuned ResNet50** model (trained on manually-labelled images) with a CLIP zero-shot fallback
- Extracts stall locations through a 5-stage pipeline: postal codes → block/street addresses → hawker centre names → neighbourhoods → stall names, backed by 250+ curated aliases (e.g. "AMK" → "Ang Mo Kio")
- Geocodes locations via **OneMap** (primary) with **Nominatim/OpenStreetMap** fallback, caching results to avoid redundant API calls
- Scores each stall using comment-level sentiment analysis with Singlish and food-specific vocabulary ("shiok", "sedap", "cmi", "wok hei")
- Generates a **single-file Leaflet map** hosted on GitHub Pages, rebuilt automatically via GitHub Actions

## The Map

- Custom Hokkien Mee bowl markers with star ratings and **MarkerCluster** density grouping
- "Near me" geolocation with Haversine distance sorting — all computed client-side
- Sidebar with real-time search, photo tabs filtered by type (noodles / storefront / other), and rich popups with photos, reaction counts, and links back to Facebook posts
- High-contrast mode, keyboard navigation, and ARIA labels

## Tech Stack

- **Python** with [uv](https://docs.astral.sh/uv/) for dependency management
- **Playwright** for headless browser scraping
- **PyTorch / TorchVision** for ResNet50 fine-tuning; **CLIP** for zero-shot fallback
- **OneMap API** and **Nominatim/OpenStreetMap** for geocoding
- **Leaflet + MarkerCluster** for the interactive map UI
- **GitHub Actions** for scheduled pipeline runs
