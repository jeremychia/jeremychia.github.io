---
layout: post
title: 'Winning mandates and creating impact - building a case for finance transformation'
image: 'https://media.licdn.com/dms/image/D4E12AQHXNNtfpulKGw/article-cover_image-shrink_720_1280/0/1701421696853?e=1727308800&v=beta&t=3uCfxc9-4tAlJkl7_zANo6edQhaYlm4YVJOku2HCYUM'
category: finance transformation
---

I'm an accountant turned data practitioner. I’ve looked at finance teams’ processes from different angles - as a front-end user, a solutions implementation consultant, and a data modeller in multinational companies and organisations of varied sizes. Finance transformation comes with its boons, but I am cognisant of the challenges its proponents face in getting buy-in from leadership in the early phases.

In this piece, I reflect on learnings from driving finance transformation initiatives. I write this considering the perspective of finance transformation leads, or analysts, who are trying to drive change. While the anecdotes are more specific to finance transformation, some reflections are intended for application to other projects which involve organisational change. Many thanks to [Professor Benyayer](https://www.linkedin.com/in/louis-david-benyayer-aa14181/?lipi=urn%3Ali%3Apage%3Ad_flagship3_pulse_read%3BegWnvOJzRmStYyBfOrr5gg%3D%3D) for the opportunity to collaborate.

# Where are finance teams now?

Finance teams are embracing change. There is a paradigm shift in how finance leaders position their teams. The change is from traditionally viewing finance teams as a compliance necessity to one that drives insights and harnesses data to create value. [PwC’s 2021 Pulse Survey](https://www.pwc.com/us/en/services/consulting/business-transformation/library/finance-effectiveness-benchmark-study.html) is telling: that 68% of CFOs in the US are investing in digital transformation.

Despite acknowledging its value, finance teams are generally in their infancy when embracing digital solutions. There is a combination of factors that explain this - hefty costs of adoption, internal resistance to change, and lack of expertise to name a few. There is a substantial amount of routine work which is still done manually. For example, copying data from one Excel spreadsheet to another. This is time-consuming and occasionally results in preventable errors.

Finance functions rely heavily on data. While traditionally, the associations are implicit, I’d like to relate data usage in finance teams to Gartner’s **analytics maturity** model. With the implementation of transactional accounting tools, finance teams have amassed a substantial volume of data.

Realistically, organisations may only be **using this data** for **descriptive** analytics and occasionally **diagnostic** analytics - think reporting, and the occasional drill-down for insights. Accenture reports that while [62% of CFOs are seeing more demand for insight from financial data, 53% worry that finance is too reactive](https://www.accenture.com/cl-es/insightsnew/operations/finance-powerhouse). There is more potential in the accumulated data which has yet to be realised.

![Gartner's analytics maturity model](https://media.licdn.com/dms/image/D4E12AQHVeVYjFEQXMw/article-inline_image-shrink_1000_1488/0/1701421504483?e=1727308800&v=beta&t=x5VmeccuI9MtkNMSZExX5AcD81u9wLyQjT3zRnsmWOU)

There is a tacit awareness that digital transformation brings benefits. The question is, how much, and how do teams get there? Finite resources (manpower, funding, etc.) point towards competing needs within an organisation. Finance transformation leads need to thread intentionally and cautiously.

# What are the possibilities for finance teams?

Transformation leads can harmonise this initiative with relevant Objectives and Key Results (OKR) within the company. Some examples include “improving scalability”, or “reducing manual touchpoints”. Initiatives positioned to address the organisation’s overarching OKRs most easily secure mandates.

The improvements finance teams can consider in the space of financial transformation can be broadly grouped into two buckets. I discuss these with finance and data professionals, and summarise them below:

## Reporting

Improve the time to report by adopting automation, reducing the need for manual actions and improving accuracy. For organisations with different accounting tools, a Finance Performance Management (FPM) tool like LucaNet, Jedox, and Anaplan helps with consolidation and ensures one source of truth (keeping data in one place).

For smaller organisations, I recommend configuring reports within the tool itself. Alternatively, leverage on data teams to build in-house solutions using the data stack - data models (built with dbt) which are exposed to visualisation tools like Looker, Power BI, or Tableau. I remember how something simple like automating graphs for use in presentations was a big time-saver in one organisation.

In the subsequent and last section, I suggest some metrics to measure success.

## Value Creation

Create insights, and inform decisions using statistical methods or machine learning. Earlier I highlighted that finance teams play host to a substantial volume of data. These historical records can be used to understand seasonality, and trends, and inform future decisions.

This data, when supplemented with other sources in the data warehouse, can be a powerful combination. This is where conversations about Cross-Planning and Analysis (XPA), a supplement to Financial Planning and Analysis come into play. For example, in a B2B or B2C setting - a combination of marketing, sales, and overhead costing could effectively inform producing pricing. The possibilities are vast.

In this regard, the Pareto Principle rings familiar: roughly 80% of consequences come from 20% of causes. Start with quick wins to build motivation and momentum with finance transformations.

Start the project by taking quantitative measurements. This is the part most teams struggle with, but I found it to be most effective in winning mandates. Throughout the project's implementation, this is one way to ensure an objective assessment of the progress. Some metrics in the reporting process to consider are:

1. Time to report after month-end (Working days)
2. Number of reworks required due to manual errors producing inaccurate or incomplete data
3. Time taken per process (Working hours), which requires the team to have a work breakdown structure of their month-end closing process prior
4. Number of finance processes involving manual work

Typically, I consider the volume of transactions to be consistent throughout the year. However, if the business is seasonal, adjust the metrics (1) and (3) accordingly.

Metrics for value creation vary by the initiative. They typically involve increasing revenue, reducing cost, improving client experience, or improving internal efficiency. In one instance where I automated one of the month-end closing processes, we managed to half the amount of time spent by reducing manual work. This was 5 FTE days saved. Seeing quantifiable progress builds confidence.

# How shall finance transformation leads continue winning mandates?

Ensure that at every step, business objectives are being met. Be certain that all stakeholders recognise the impacts and benefits as well. Be mindful that ultimately, the aims of financial reporting with the [Conceptual Framework for Financial Reporting](https://www.iasplus.com/en/standards/other/framework) should be met. This means that the information should be relevant, faithfully represented, and timely amongst others.

Reinforce that finance transformation is a journey. It is not a means to an end, but a process of *Kaizen* (continuous improvement). Build a roadmap where impacts are obvious. This will keep stakeholders excited and engaged. At the same time, there may be a tendency to want to be everything everywhere all at once. There is a need to reign in and prioritise competing needs.

Building trust is important. Accenture’s report on future-ready finance reports that 27% of finance leaders say that [inconsistent, inaccurate or inaccessible data is preventing them from realising their full potential](https://www.accenture.com/us-en/insights/operations/future-ready-finance) as drivers of strategic change.

Borrowing inspiration from data best practices: once data models are set up, building tests ensures faithful representation. In the finance world, this is called internal controls. For data practitioners, this can look like unit testing, row-level expressions tests, or column-level tests. In data models, these can look like:

* **Unique values tests**: to ensure line items are not double-counted; no duplicates.
* **Accepted value tests**: to ensure that the data is classified properly and produces expected results. For example, a cost centre or supplier account is correctly indicated.
* **Reasonableness tests**: that values are within expectations (e.g. margins should be within a certain range, revenue should be positive, etc.)
* **Freshness tests**: to ensure that the data generated is recent and complete, that the data pipeline is working and delivers updated information.

The tests can prevent errors from compounding. In one implementation, with the presence of a unique value test, the team caught a faulty join which was causing transactions to duplicate.

There is even a possibility to go further to use distributions of revenue or expenses in previous months to ascertain that the results reported are within expectations.

# The change at stake

## Process changes

Acknowledging that finance transformation is an exercise of change management is essential. Consider too, that the persons undergoing this change have varied priorities. There are finance practitioners who are excited and ready to embrace change, but there are those who are resistant. At one point, the predominant chatter was about how [automation would replace accounting jobs](https://jgbc.fiu.edu/index.php/Home/article/download/233/182/#:~:text=According%20to%20their%20findings%2C%20accountants,Jobs%20Susceptible%20to%20Automation.). In implementing finance transformation, I walked into many projects having to first establish that the change coming is an exciting opportunity to reduce laborious work which finance teams did not enjoy so that the upsides could be focused on.

I find the ADKAR Change Management Model useful for considering how to approach the situation. To acknowledge hesitation or resistance, I found [Kübler Ross' Change Curve Model](https://www.taylorfrancis.com/books/mono/10.4324/9780203010495/death-dying-elisabeth-k%C3%BCbler-ross) to be a good way to approach the situation empathetically.

![ADKAR Change Management Mode](https://media.licdn.com/dms/image/D4E12AQGXRZNExj3weA/article-inline_image-shrink_1500_2232/0/1701421604436?e=1727308800&v=beta&t=04qCLP5yVdmwn4t_Ex2ptRw8llypJTOw7yNl14PMZEE)

## People upskilling

At the heart of the project, it is core to acknowledge individual actors’ roles in ensuring success. Their legitimate concerns, motivations, and sentiments are crucial. Investing in training people in new tools and ways of thinking provides assurance and keeps team members engaged.

Organisations can embrace a [skills-first framework](https://www.pwc.com/gx/en/issues/upskilling/first-skills-report/report/WEF_CNES_Putting_Skills_First.pdf) as proposed by the World Economic Forum. These involve identifying skills needed and charting roadmaps for each individual. Some examples include data literacy, accounting information systems, and automation. [Gartner](https://www.gartner.com/smarterwithgartner/fill-finances-skill-gaps), and [ACCA](https://www.accaglobal.com/gb/en/technical-activities/technical-resources-search/2014/december/finance-transformation-roles.html), amongst others, have elaborated on this.

Teams should also be prepared to invest more in employee training to bridge the gap. The median learning and development hours stand at 10.1 hours per full-time employee, with a median cost of 850 EUR (US$907). According to [PwC’s 2021 Finance Effectiveness Benchmarking Study](https://www.pwc.com/us/en/services/consulting/business-transformation/library/finance-effectiveness-benchmark-study.html), firms that invest heavily in upskilling have 27% lower turnover than organisations that do not invest as heavily.

There is apprehension, but the effects are positive. There was an exchange which goes: *“What happens if we invest in developing our people and then they leave us?”* and the response *“What happens if we don’t, and they stay?”*.

## Data Quality

Data quality remains at the heart of finance transformation effectiveness. In the [IBM 2021 Global C-Suite Study](https://www.fm-magazine.com/news/2021/apr/data-quality-stresses-for-finance.html), 70% of leading CFOs say implementing enterprise-wide data standards is a top priority. These efforts to standardise data and improve quality will have positive spillover effects throughout the organisation.

For finance applications, building more (time) buffers to get data right is necessary. While launching data initiatives for finance teams, controllers were quick to stress the need for accurate data. I remember spending twice the amount of time trying to get the data right due to fixing edge cases as compared to rolling out the first iteration of the features. While it sometimes contradicts the Pareto principle in prioritisation, this is necessary due to the use cases for financial data in reporting.

It is important to make data quality intentional and obvious. After all, the saying about data goes: “Garbage in, garbage out”.

# A final note

While the possibilities are limitless, solving pain points and business problems takes precedence over tools. In Gartner's analytics maturity model, different organisations naturally find themselves at different stages. There should not be a need to force a solution onto an unready team. A foundation must be built before progressing. An exaggerated antithesis is an organisation with messy data which wants to do predictive modelling. Pay close attention to data quality and the fundamentals. Be aware of what the tools can do and be intentional in the application of such tools.

Securing mandates, winning minds, and building trust are elements of a finance transformation project which finance and data practitioners are well-prepared to enact.
