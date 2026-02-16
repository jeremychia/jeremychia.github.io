---
layout: project
title: Singapore Parliament Speeches
image: "/assets/images/projects/parlehmate.png"
category: Data Pipeline
featured: true
tags:
  - politics
  - python
  - dbt
  - streamlit
excerpt: >
  A full-stack data pipeline that scrapes, transforms, and visualizes 20+ years of Singapore parliamentary debates — making civic data accessible to researchers and citizens.
business_problem: >
  Singapore's parliamentary records are publicly available, but buried in PDFs and HTML pages that are difficult to search or analyze. Researchers and journalists had no way to easily track voting patterns, topic trends, or MP participation over time.
modeling_logic: >
  Built a three-layer pipeline: **Python scrapers** extract raw HTML from parliament.gov.sg, **dbt models** clean and structure the data into a star schema (fact_speeches, dim_members, dim_topics), and a **Streamlit app** serves interactive visualizations.
impact: >
  - **40,000+ speeches** indexed and searchable
  
  - Used by academic researchers at NUS and SMU
  
  - Featured in local civic tech community discussions
links:
  - title: GitHub
    url: https://github.com/jeremychia/singapore-parliament-speeches
---

Together with friends, in consultation with researchers and members of civic society, I've put together a pipeline for scraping and modeling data from the Singapore Parliament. This was driven by a desire to make parliamentary data more accessible for Singaporeans.

## Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Python Scraper │────▶│   dbt Models    │────▶│   Streamlit     │
│  (Extraction)   │     │  (Transform)    │     │  (Visualize)    │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

## Components

* [Data Extraction using Python](https://www.github.com/jeremychia/singapore-parliament-speeches)
* [Data Transformation with dbt](https://www.github.com/jeremychia/singapore-parliament-speeches-dbt)
* [Data Visualisation on Streamlit](https://www.github.com/jeremychia/singapore-parliament-speeches-streamlit)
