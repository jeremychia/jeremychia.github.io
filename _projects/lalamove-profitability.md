---
layout: project
title: "Lalamove Profitability Calculator"
image: "/assets/images/projects/lalamove-profitability.png"
featured: true
category: Web App
tags:
  - javascript
  - api
  - singapore
  - gig-economy
links:
  - title: Live Site
    url: https://jeremychia.github.io/lalamove-profitability/
  - title: GitHub
    url: https://github.com/jeremychia/lalamove-profitability
---

A mobile-first tool for Singapore motorcycle delivery riders to decide — in under 30 seconds — whether a Lalamove order is worth taking.

Built from personal experience as a part-time delivery rider, it models all the variables that matter: real road distances, wait times by building type, peak-hour traffic, and Lalamove's full deduction stack (15% commission + 9% GST + $0.50 platform fee).

## Core Calculator

- **Multi-stop route calculation** via OneMap's routing API, with a straight-line × 1.4 fallback when the API is unavailable
- **GPS support** — tap to fill your current location via the browser Geolocation API
- **Fuel cost** based on your motorcycle model (10+ pre-configured bikes from YBR125 to PCX160, or enter your own km/L)
- **Wait time estimation** by building type — HDB (3 min), landed (2 min), condo (7 min), office (10 min), mall (8 min) — with time-of-day adjustments for lunch and dinner rushes
- **Traffic awareness** — auto-detects Singapore peak hours and adjusts travel speeds accordingly
- **$/hour rating** with a four-tier verdict: Excellent ($20+/hr), Good ($15+), Okay ($10+), Poor

## Fare Breakdown

The calculator decomposes exactly what gets deducted before you're paid:

| Deduction | Amount |
|-----------|--------|
| Platform fee | −$0.50 (flat) |
| Commission | −15% of base fare |
| GST | −9% of base fare |

Net profit is then compared against fuel cost to produce the final hourly rate.

## Efficiency Guide

A companion page explains *why* multi-stop orders are disproportionately profitable: each additional stop adds ~$3 gross ($2.28 net) for roughly 5 minutes of extra wait — equivalent to $27/hr for that leg alone. The guide includes scenario comparisons across common order types and a building-type wait-time reference.

## Tech Stack

- **Vanilla JavaScript** (ES Modules) — no framework, ~25KB total
- **OneMap Singapore API** for geocoding and routing
- **GitHub Actions** for CI/CD with secrets injection into `secrets.js`
- **GitHub Pages** for hosting
