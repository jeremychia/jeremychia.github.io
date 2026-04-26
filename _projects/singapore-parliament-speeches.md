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
---

A three-part pipeline to scrape, model, and visualise Singapore's parliamentary debate records — built with friends in consultation with civic researchers, to make Hansard data more accessible to Singaporeans.

- **[Data Extraction](https://www.github.com/jeremychia/singapore-parliament-speeches)** — Python scraper against the Parliament Reports Search (SPRS) API
- **[Data Transformation](https://www.github.com/jeremychia/singapore-parliament-speeches-dbt)** — dbt models for cleaning and structuring the data
- **[Data Visualisation](https://www.github.com/jeremychia/singapore-parliament-speeches-streamlit)** — Streamlit dashboard for exploration

## What It Collects

The scraper pulls ~41,837 parliamentary records across 23+ document types: oral and written answers, ministerial statements, bills, budget debates, motions, adjournment matters, and more. For each record it captures the full HTML content, sitting metadata (parliament number, date, volume), speaker attribution, and linked attachments.

Each HTML document is then converted to Markdown and parsed for individual speeches — extracting speaker names and transcript content using regex against bold-marker patterns, with a confidence tracking layer that flags records where parsing was incomplete.

## Pipeline Architecture

| Stage | What happens |
|-------|-------------|
| **Fetch** | Paginated API calls (~20 results/page, ~2,092 pages) with date-range filtering for incremental loads |
| **Store raw** | Full API responses saved to PostgreSQL via SQLModel ORM |
| **Process** | HTML → Markdown conversion, title/subtitle parsing, type casting |
| **Extract speeches** | Speaker-level splitting from Markdown, linked back to parent records |
| **QA** | Parsing statistics table tracks success rates at each stage |

The pipeline is designed for incremental runs — each stage is independently re-runnable, so only new sittings need to be fetched and processed on subsequent executions.

## Tech Stack

- **Python** with Poetry, SQLModel (Pydantic + SQLAlchemy), and BeautifulSoup
- **PostgreSQL** for structured storage
- **html2text** for HTML-to-Markdown conversion
- **dbt** for downstream data modelling
- **Streamlit** for the analytics interface
