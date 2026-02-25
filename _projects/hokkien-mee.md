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

An end-to-end pipeline that turns posts from the **Hokkien Mee Hunting** Facebook group into an interactive map of Hokkien Mee stalls across Singapore.

## What it does

- Scrapes public group posts (with your exported cookies) using Playwright
- Extracts structured data (text, locations, images, reactions, comments)
- Geocodes stall locations with OneMap (plus OpenStreetMap fallback)
- Computes post-based signals to highlight more-discussed stalls
- Generates a single-page **Leaflet** map (hosted on GitHub Pages) with:
  - Custom Hokkien Mee bowl markers
  - "Near me" geolocation and distance sorting
  - Sidebar listing stalls, search, and sort options
  - Rich popups with photos, reactions, and deep links back to Facebook

## Tech Stack

- **Python** with [uv](https://docs.astral.sh/uv/) for dependency management
- **Playwright** for headless browser scraping
- **OneMap API** and **Nominatim/OpenStreetMap** for geocoding
- **Leaflet + MarkerCluster** for the interactive map UI
- **GitHub Pages** for hosting the final map at `/hokkien-mee/`
