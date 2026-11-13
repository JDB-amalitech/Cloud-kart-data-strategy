# Kloud Kart – Reporting and Data Management Diagrams

## Overview

This folder contains supporting architecture and process diagrams for the proposed improvement of Kloud Kart's reporting, data management, system reliability and data protection.

The diagrams are designed to help management and technical staff understand the current challenges, proposed solutions and 12-month implementation roadmap.

## Diagrams Included

| No. | Diagram | Purpose |
|---|---|---|
| 1 | Current Reporting Problem | Explains how using one MySQL server for both business operations and reporting can affect website performance. |
| 2 | Proposed Data Architecture | Shows the proposed flow from MySQL Production through a Read Replica and Python ETL into PostgreSQL and Power BI. |
| 3 | Proposed Data Architecture | Shows the proposed flow from MySQL Production through a Read Replica and Python ETL into PostgreSQL and Power BI. |
| 4| Data-platform | Explains the differences between each Data platform  |
| 5 | Monday Reporting Reconciliation | Explains the reporting validation process and the responsibilities of the technical and business teams. |

## Proposed Data Architecture

The recommended reporting architecture is:

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

**Important:** The read replica is prioritised in Q1. PostgreSQL warehouse implementation is planned for Q4, subject to the Q3 infrastructure, capacity and cost assessment.

Live website transactions and stock availability checks will continue using the production MySQL database.

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
| PostgreSQL | Central reporting data warehouse |
| Power BI | Dashboards and management reporting |
| Draw.io | Architecture and process diagrams |

## How to Open and Edit the Diagrams

1. Click on diagrams folder
2. Select the diagrams from the dropdown list 
3. Double click it to open


You can also export diagrams as PNG, SVG or PDF for inclusion in reports and presentations.

## Important Considerations

- The proposed architecture is a phased recommendation, not a claim that all components are already implemented.
- PostgreSQL procurement should follow the Q3 assessment.
- Data protection controls require appropriate policies, implementation and qualified professional advice.
- The Monday reconciliation process should be aligned with the company's actual reporting template and Finance's approved definitions.
- Forecasting and advanced analytics should only be introduced when reliable data and a clear business need justify them.

## Prepared By

**Joseph Danquah Botchway**

**Project:** Kloud Kart – Reporting and Data Management Improvement Proposal

**Date:** November 2026