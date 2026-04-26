---
layout: project
title: "Singapore Budget Speeches Analysis"
image: "/assets/images/projects/singapore-budget-speeches.png"
category: Analysis
tags:
  - politics
  - nlp
  - python
  - data-analysis
links:
  - title: GitHub
    url: https://github.com/parleh-mate/singapore-budget-speeches
---

Interactive exploration of **65 years of Singapore's fiscal policy** through 40,123 sentences from 66 budget speeches (1960–2025).

## At a Glance

- **7 Finance Ministers** analysed from Goh Keng Swee to Lawrence Wong
- **15 ministry classifications** tracking policy focus across 7 decades
- **4 major economic crises** with quantified policy response shifts
- Linguistic analysis tracking how readability and sentence complexity evolved over time

## How It Works

Speeches are scraped from the Parliament Hansard and sentence-tokenised using **spaCy**. Each sentence is then classified into one of 15 ministry categories using a weighted keyword matching system — multi-word terms (e.g. "national service") score higher than single words — achieving 82.7% classification coverage across all sentences. The remaining 17.3% are labelled "general".

Analysis notebooks produce CSV datasets; an export script shards these into decade-level JSON files for progressive loading on the web front-end.

## Key Findings

| Era | Period | Dominant Focus |
|-----|--------|----------------|
| Survival & Security | 1960s–70s | Defence at 19.8% — industrialisation, nation-building |
| Economic Transformation | 1980s–90s | Finance at 17.4% — services economy, crisis responses |
| Inclusive Growth | 2000s–10s | Manpower at 9.2% — CPF reforms, social safety nets |
| Sustainable Future | 2020s | Sustainability at 4.1% — climate, digital transformation |

Crisis response patterns are measurable: the 1997 Asian Crisis triggered the highest Finance spike (+5.3pp), while COVID-19 shifted emphasis toward Health (+1.9pp) and Social & Family (+1.1pp).

Speeches also got more accessible over time — average sentence length fell from 21.0 words in the 1960s to 18.1 words today.

## The Website

A six-page static site built with vanilla JavaScript and Plotly.js, designed for three audiences:

- **The Storyteller** (5 min) — curated narrative with key insights
- **The Explorer** (15 min) — interactive charts by topic and minister
- **The Researcher** (30+ min) — full-text search across 39,704 sentences with decade, minister, and ministry filters

## Tech Stack

- **Python** with Poetry for dependency management
- **spaCy** for sentence tokenisation and linguistic metrics
- **Pandas / Parquet** for data storage and analysis
- **Jupyter Notebooks** for exploratory analysis
- **Plotly.js** for interactive charts
- **GitHub Pages** for the interactive website
