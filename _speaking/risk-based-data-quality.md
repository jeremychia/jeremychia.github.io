---
layout: project
title: Test Smarter, Not Harder
image: https://img.youtube.com/vi/tNZMm4KTjTc/maxresdefault.jpg
category: Forward Data Conference
video: https://www.youtube.com/watch?v=tNZMm4KTjTc
tags:
  - dbt
  - data-quality
  - risk-management
---

How we transformed data testing at Vinted from reactive firefighting to a proactive, risk-based framework using materiality concepts from accounting.

## The Problem

After migrating to a left-shifted testing model — validating data at the source with null checks, accepted values, and expression tests — Vinted's finance pipelines went from consistently high daily success rates to significantly lower within two months. Upstream schema changes were breaking pipelines daily. Overly strict tests meant that even localised issues with a single incoming invoice could halt critical reporting, eroding stakeholder trust and causing alert fatigue.

## The Solution

We introduced a risk-based testing framework inspired by financial auditing materiality concepts, categorising every test by **impact** and **frequency**:

| Quadrant | Response |
|----------|----------|
| High impact / High frequency | Maintain strict testing — avoid at all costs |
| High impact / Low frequency | Prevent with targeted checks |
| Low impact / High frequency | Monitor without blocking daily runs |
| Low impact / Low frequency | Accept, review periodically |

**Implementation with dbt and Airflow:**

Tests were tagged by risk category (e.g., `highimpact_highfrequency`, `lowimpact_lowfrequency`). The Airflow orchestration reads `+meta.excluded_tests` configuration and converts it into `--exclude` flags at the dbt CLI:

```bash
dbt build --exclude tag:lowimpact_highfrequency tag:lowimpact_lowfrequency
```

This split execution into two tracks:
- **Main pipeline run** — only high-impact tests block execution
- **Monitoring run** — low-impact tests fire separately, generating alerts for weekly review

**Change management:**

We stress-tested the idea through an RFC process — recognising the problem, gathering stakeholder requirements, and aligning collaboratively before acting. Actionable alerts build trust; noisy alerts erode it.

## The Result

- Reduced misstatement risk from €40M to €4M
- Caught €1.6M in carrier overcharges
- Pipeline DAGs became leaner with faster execution times
- Daily success rates stabilised and stakeholder confidence recovered
- Engineers no longer dread weekend alerts

[Watch the talk →](https://www.youtube.com/watch?v=tNZMm4KTjTc)

[Read the Vinted Engineering writeup →](https://vinted.engineering/2026/03/11/risk-based-testing/)
