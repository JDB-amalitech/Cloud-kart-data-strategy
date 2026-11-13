# Kloud Kart – Reporting and Data Management Improvement Proposal

## Overview

This repository contains a proposed plan to improve Kloud Kart's reporting, data management, website reliability and customer-data protection over the next 12 months, including preparation for the Nigeria expansion.

It is a phased **recommendation**. It does not claim that any component is already implemented.

## Repository Structure

| Path | Contents |
|---|---|
| `client-memo.md` | One-page cover memo to Nana: what was found, built and recommended, and what could not be stood behind. |
| `Situation_diagnosis.md` | Root causes, business impact and risk ranking. |
| `Recommendation.md` | Recommended architecture, technology choices and data-protection measures. |
| `Roadmap.md` | 12-month implementation roadmap with outcomes Nana can verify each quarter. |
| `Decisions/` | Six Architecture Decision Records (ADR-001 to ADR-006), all currently **Proposed** pending client review. |
| `Decisions/improvement/improvement.md` | 12-month improvement plan for the existing PHP/MySQL developer. |
| `Diagrams/` | Supporting diagrams (see below). |

## Diagrams

| File | Purpose |
|---|---|
| `Current_setup.png` | Today's set-up: one MySQL server serving the website, Nana and Finance. |
| `kloud_kart_proposed_data_architecture.png` | Proposed flow from MySQL production through a read replica and Python ETL to the data warehouse and Power BI. |
| `Implementation_Roadmap.png` | The 12-month roadmap on one page, with the target data flow. |
| `Datawarehouse.png` | Illustration of how a data warehouse works. |
| `Datalake.png` | Illustration of a data lake architecture, used to explain why a lake was deferred. Third-party image: see "Image sources" below. |

## Proposed Data Architecture

```text
MySQL Production
       |
       v
MySQL Read Replica
       |
       v
Python ETL Pipeline
       |
       v
PostgreSQL Data Warehouse
       |
       v
Power BI
```

**Important:** The read replica is prioritised in Q1. The PostgreSQL data warehouse is planned for Q4, subject to the Q3 infrastructure, capacity and cost assessment.

Live website transactions and stock availability checks continue to use the production MySQL database.

## Implementation Roadmap

- **Q1 – Stabilisation:** Recruit a Data Engineer, configure the read replica and automate reporting extraction.
- **Q2 – Reporting Improvement:** Recruit a Data Analyst/BI Developer, improve reconciliation and develop dashboards.
- **Q3 – Nigeria Preparation:** Review reporting requirements, data quality, infrastructure capacity and costs.
- **Q4 – Data Warehouse:** Implement PostgreSQL, integrate Python ETL and connect Power BI.

## Technology Stack

| Technology | Purpose |
|---|---|
| MySQL | Existing operational database |
| MySQL Read Replica | Separates reporting reads from production workloads |
| Python | Data extraction, transformation and validation |
| PostgreSQL | Central reporting data warehouse (Q4, subject to Q3 review) |
| Power BI | Dashboards and management reporting |

## Important Considerations

- PostgreSQL procurement follows the Q3 assessment.
- Infrastructure costs need supplier quotations; system capacity needs workload testing.
- Data protection controls require appropriate policies, implementation and qualified professional advice. A register alone does not establish compliance.
- Cross-border processing for Nigeria needs legal and regulatory assessment.
- The Monday reconciliation process should be aligned with the company's actual reporting template and Finance's approved definitions.
- Forecasting and advanced analytics should only be introduced when reliable data and a clear business need justify them.

## Image sources

`Datalake.png` carries an Altexsoft logo and appears to be taken from Altexsoft's published material. Cite it (source and URL) or replace it with an original diagram before the repository is shared beyond the client.

## Prepared By

**Joseph Danquah Botchway**

**Project:** Kloud Kart – Reporting and Data Management Improvement Proposal

**Date:** November 2026
