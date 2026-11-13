# ADR-006: Recruit a Data Engineer in Month 1 and a Data Analyst/BI Developer in Month 4

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Proposed: Kloud Kart leadership.

## Context

Kloud Kart currently has one PHP/MySQL developer but lacks dedicated data engineering and business intelligence capacity.

The company has a limited budget for two data-related hires and needs to establish a reporting environment, automate data processing, improve business reporting and strengthen customer-data governance.

The order of recruitment is important because reliable reporting depends on a properly configured data environment.

The 12-month implementation roadmap identifies two recruitment stages:

- Month 1: Data Engineer.
- Month 4: Data Analyst/BI Developer.

## Decision

Recruit two data professionals according to the implementation roadmap.

### First hire: Data Engineer – Month 1

The Data Engineer will:

- Configure the MySQL read replica.
- Establish replication monitoring and alerts.
- Develop automated Python ETL pipelines.
- Implement incremental extraction and data validation.
- Prepare controlled reporting datasets for Power BI.
- Support warehouse assessment and Q4 PostgreSQL implementation.
- Support technical data protection, backup and recovery controls.

### Second hire: Data Analyst/BI Developer – Month 4

The Data Analyst/BI Developer will:

- Standardise business reporting definitions.
- Reconcile Finance and Operations figures.
- Develop and maintain Power BI dashboards.
- Establish reporting data-quality checks.
- Support customer-data export tracking and governance documentation.
- Help prepare consistent reporting across Ghana and Nigeria.

The existing PHP/MySQL developer will continue supporting the website and operational database integration.

Management will retain privacy accountability and obtain appropriate external legal or data-protection advice where necessary.

## Alternatives considered

### Alternative A: Recruit a Data Analyst/BI Developer first

- **How it would work:** Hire the reporting specialist before establishing the new reporting infrastructure.
- **Why it is attractive:** Management could receive improved dashboards and reporting support earlier.
- **Why rejected:** The existing production database performance problem would remain unresolved, and the analyst could still depend on unreliable manual exports.

### Alternative B: Recruit two Data Engineers

- **How it would work:** Use both recruitment positions for infrastructure and pipeline development.
- **Why it is attractive:** It would increase engineering capacity for database replication, ETL and warehouse implementation.
- **Why rejected:** It would leave no dedicated capacity for business reporting, dashboard development, metric standardisation and governance coordination.

### Alternative C: Recruit a Data Engineer in Month 1 and a Data Analyst/BI Developer in Month 4

- **How it would work:** Establish reliable data infrastructure first, then recruit the reporting specialist to improve business intelligence and governance.
- **Why it is attractive:** It follows the technical dependency between data infrastructure and reliable reporting.
- **Why selected:** It matches the two-hire budget and the 12-month implementation roadmap.

## Consequences

- **What this buys:** Dedicated infrastructure ownership, automated reporting, consistent business definitions and stronger governance coordination.
- **What this costs:** Two salaries, recruitment expenses, onboarding and time from the existing developer and departmental representatives.
- **What it costs the client if I am wrong:** If business reporting is more urgent than infrastructure, delaying the analyst may prolong manual reporting. If the second recruitment is delayed, governance and dashboard improvements may also take longer.
- **What would make me revisit this:** Evidence that a reliable external provider can establish and maintain the infrastructure more economically, or that business reporting and governance risks have become more urgent than engineering requirements.

## What this survives

This decision survives pressure to hire dashboard developers before fixing the underlying data environment.

Dashboards cannot resolve inconsistent reporting definitions or unreliable source data on their own.

Recruiting the Data Engineer first addresses the immediate infrastructure problem. Recruiting the Data Analyst/BI Developer in Month 4 ensures that the company can then turn reliable data into useful business information.

The recruitment plan must remain within the approved two-hire budget.