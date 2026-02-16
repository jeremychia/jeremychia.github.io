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

A web-based tool for **Singapore motorcycle delivery riders** to quickly assess whether a Lalamove order is worth taking.

## Features

### Core Calculator
- 📍 **Multi-stop route calculation** using Singapore's OneMap API
- 📱 **GPS location support** — tap to use your current location
- ⛽ **Fuel cost estimation** based on your motorcycle model (10+ bikes supported)
- ⏱️ **Smart wait time prediction** based on building type (HDB, condo, office, mall, etc.)
- 🚦 **Traffic-aware timing** — auto-detects peak hours in Singapore
- 💰 **Profitability rating** with $/hour breakdown

### Fare Breakdown
- 💵 **Lalamove deductions breakdown** — see exactly what you earn:
  - 15% commission (on base fare)
  - 9% VAT/GST
  - $0.50 platform fee offset
  - CPF withholding (placeholder for Platform Worker's Act)
- 📊 **Net profit calculation** after all deductions and fuel costs

### Efficiency Guide
- 📈 **Multi-stop efficiency analysis** — understand why 2-3 stop orders pay better
- 🎯 **Scenario comparisons** — see $/hour for typical order types
- ✅ **Decision framework** — quick take/consider/avoid guidelines
- 🏢 **Wait time reference** by building type

### User Experience
- 🗺️ **Open in Google Maps** — one tap to navigate your route
- 🏷️ **Building type badges** — see HDB/Condo/Office inside inputs
- 📱 **Mobile-optimized** — compact single-line layout for small screens
- ⚙️ **Customizable settings** — petrol price, bike model, API token

## How It Works

1. **Enter locations** — your current location (or tap 📍 for GPS), pickup, and delivery stops
2. **Enter the fare** — the amount shown in Lalamove app
3. **Get instant analysis** — profitability rating, fare breakdown, and $/hour

## Tech Stack

- **Vanilla JavaScript** (ES Modules)
- **OneMap Singapore API** for geocoding & routing
- **GitHub Pages** for hosting
- **GitHub Actions** for CI/CD with secrets injection

## Project Structure

```
docs/
├── index.html          # Main calculator
├── guide.html          # Efficiency guide page
├── style.css           # Mobile-first styles
└── js/
    ├── main.js         # App entry point
    ├── config.js       # Constants & configuration
    ├── api/            # OneMap API client
    ├── services/       # Business logic (routing, fuel, profitability)
    ├── ui/             # UI components & rendering
    └── utils/          # Validation & formatting
```

## Background

This project was born from my experience as a part-time delivery rider. I wanted to understand which orders were truly profitable after accounting for fuel, time, and platform fees. The calculator helps riders make data-driven decisions in real-time.
