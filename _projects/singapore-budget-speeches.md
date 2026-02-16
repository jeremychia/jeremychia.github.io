---
layout: project
title: "Singapore Budget Speeches Analysis"
image: "/assets/images/main.avif"
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

Interactive exploration of **65 years of Singapore's fiscal policy** through 40,000+ sentences from budget speeches.

## At a Glance

- **40,123 sentences** from 66 budget speeches (1960-2025)
- **7 Finance Ministers** from Goh Keng Swee to Lawrence Wong
- **15 Ministry classifications** (Defence, Finance, Education, Health, etc.)
- Linguistic analysis tracking readability and complexity evolution
- Crisis response patterns analyzing 4 major economic crises

## Key Findings

### Singapore's Policy Evolution

| Era | Period | Focus |
|-----|--------|-------|
| **Survival & Security** | 1960s-1970s | Defence 19.8%, industrialization, nation-building |
| **Economic Transformation** | 1980s-1990s | Finance 17.4%, services economy, crisis responses |
| **Inclusive Growth** | 2000s-2010s | Manpower 9.2%, healthcare, social safety nets |
| **Sustainable Future** | 2020s | Environment 4.1%, digital, climate action |

### Finance Minister Comparison

| Minister | Tenure | Top Focus | Archetype |
|----------|--------|-----------|-----------|
| Goh Keng Swee | 1959-1984 | Defence (25.2%) | The Architect |
| Richard Hu | 1985-2001 | Finance (19.3%) | The Prudent Steward |
| Tharman Shanmugaratnam | 2007-2015 | Manpower (9.2%) | The Social Reformer |
| Heng Swee Keat | 2015-2021 | Manpower (9.8%) | The Inclusivity Champion |
| Lawrence Wong | 2021-2025 | Sustainability (4.1%) | The Sustainability Advocate |

## Project Components

| Component | Description |
|-----------|-------------|
| `extractor/` | Web scraping from Parliament Hansard |
| `processor/` | Markdown → structured data pipeline using spaCy |
| `analysis/` | Jupyter notebooks & key findings |
| `output_markdown/` | Raw speeches (66 markdown files) |
| `output_processor/` | Processed Parquet datasets |
| `docs/` | Interactive website |

## Methodology

1. **Extraction** — Scrape from Parliament Hansard
2. **Processing** — Sentence tokenization with spaCy
3. **Classification** — 15 ministry categories (82.7% accuracy)
4. **Analysis** — Linguistic metrics, crisis patterns

## Tech Stack

- **Python** with Poetry for dependency management
- **spaCy** for NLP processing
- **Pandas/Parquet** for data storage
- **Jupyter Notebooks** for analysis
- **GitHub Pages** for interactive website

## Usage Example

```python
import pandas as pd

# Load sentence data
df = pd.read_parquet('output_processor/2020.parquet')

# Search for keywords
healthcare = df[df['sentence_text'].str.contains('healthcare', case=False)]

# Load ministry trends
ministry_trends = pd.read_csv('analysis/ministry_by_year.csv', index_col=0)
ministry_trends['defence'].plot(title='Defence Prominence Over Time')
```
