---
layout: project
title: "Personal Finance Data Pipeline"
image: "/assets/images/projects/personal_finances.png"
featured: true
category: Data Engineering
tags:
  - dbt
  - bigquery
  - python
  - analytics
links:
  - title: GitHub
    url: https://github.com/jeremychia/personal-finances-dbt
---

A **dbt** project on BigQuery that consolidates financial data from 20+ banks and investment platforms — across Singapore, Germany, France, Hong Kong, the UK, and the US — into a single analytics-ready data warehouse.

The hard problem it solves isn't the dashboards; it's the consolidation layer itself: unifying heterogeneous transaction formats, handling seven currencies, and correctly separating investment returns from FX gains.

## Data Model

The project follows a medallion architecture across five layers:

| Layer | What it contains |
|-------|-----------------|
| **Staging** | Institution-specific normalization — date parsing, type casting, amount calculations |
| **Facts** | Unified transaction ledger, daily portfolio snapshots, FX rate history |
| **Dimensions** | 3-level expense hierarchy (category → subcategory → type), date spine |
| **Marts** | Analytics-ready tables for spending, balances, and investment performance |

All 23 bank staging models are unioned into a single fact table via `dbt_utils.union_relations()`.

## Multi-Currency FX Architecture

For each transaction and balance, the pipeline distinguishes between two types of gain:

- **Investment gain** — change in the asset's underlying value
- **FX gain** — change due to currency movements

This is achieved by preserving the spot-rate cost basis at transaction time alongside the current-rate balance. The difference is the unrealised FX gain. For hybrid HKD/USD portfolios, cost basis is allocated proportionally across currencies before attribution.

Exchange rates come from two sources: direct SGD cross-rates (from a Google Sheets input) and ECB EUR rates, with forward-fill logic for weekends and holidays.

## Supported Institutions

**Singapore:** DBS, UOB, OCBC, HSBC, Citi, Standard Chartered, Revolut, Wise

**Europe:** N26, AMEX Payback/Rose Metal/Miles & More (Germany), HSBC France, Wise GBP

**Asia-Pacific:** Hang Seng Bank (HK), Wise HKD

**Investments:** CDP equities, USD/HKD portfolios, Funding Societies P2P lending

## Tech Stack

- **dbt** with `dbt-utils`, `dbt-date`, `dbt-external-tables`
- **BigQuery** as the data warehouse
- **Google Sheets** as the data ingestion layer (offline reconciliation, no bank API coupling)
- **SQLFluff / sqlfmt** for SQL linting and formatting
- **GitHub Actions** for CI/CD — automatically builds dbt docs and deploys to GitHub Pages
- **Pre-commit hooks** for schema documentation enforcement and secret detection
