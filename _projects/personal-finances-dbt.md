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

A comprehensive **dbt** (data build tool) project designed to manage, transform, and analyze personal financial data across multiple currencies, countries, and financial institutions.

## Overview

This project creates a unified data warehouse for tracking expenses, investments, and balances with proper foreign exchange handling and categorization.

### Key Features

- **Multi-currency support** — Primary focus on SGD with EUR, USD, HKD conversions
- **Investment analytics** — Market value vs. cost basis with P&L calculations
- **Expense categorization** — Hierarchical expense categories (category → category2 → category3)
- **Balance tracking** — Daily snapshots across bank accounts, credit cards, and investment platforms
- **FX gain/loss tracking** — Separate calculation of currency vs. investment gains

## Architecture

The project follows a layered data architecture:

```
Sources → Staging → Facts/Dimensions → Marts
```

### Data Model Structure

| Layer | Purpose |
|-------|---------|
| **Staging** | Raw data transformation and standardization |
| **Facts** | Core business events (transactions, balances, FX rates) |
| **Dimensions** | Reference data (categories, dates) |
| **Marts** | Business-ready analytics tables |

## Supported Institutions

### Singapore
- **Banks:** DBS, UOB, OCBC, HSBC
- **Credit Cards:** Citi, Standard Chartered, UOB, HSBC
- **Digital:** Revolut, Wise

### International
- **Germany:** N26, AMEX (Payback, Rose Gold, Miles & More)
- **France:** HSBC France
- **Hong Kong:** Hang Seng Bank
- **UK/US:** Wise multi-currency accounts

### Investment Platforms
- Local SGD investments
- USD-denominated investments
- CDP (Central Depository) accounts
- FundingSocieties P2P lending

## Tech Stack

- **dbt** for data transformation
- **BigQuery** as the data warehouse
- **Python/Poetry** for dependency management
- **SQLFluff** for SQL linting
- **Pre-commit hooks** for code quality

## Sample Queries

```sql
-- Monthly spending by category
SELECT
    FORMAT_DATE('%Y-%m', local_date) AS month,
    category2,
    SUM(sgd_amount) AS total_sgd
FROM mart_sgd_bank_transactions
WHERE category3 = 'Expense'
GROUP BY 1, 2
ORDER BY 1 DESC, 3 DESC;

-- Net worth tracking
SELECT
    local_date,
    SUM(sgd_balance) AS total_net_worth_sgd
FROM mart_sgd_balances
GROUP BY 1
ORDER BY 1;
```
