# ADR-002: Introduce a PostgreSQL data warehouse in Q4

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Proposed: Kloud Kart leadership, with the Data Engineer responsible for technical assessment and implementation.

## Context

Kloud Kart needs a reliable analytical environment that can support management reporting, historical analysis and future expansion into Nigeria.

The current production MySQL database is designed to support operational activities rather than serve as the company's long-term analytical platform.

The company requires a structured reporting environment that allows Finance, Operations and management to work with consistent business figures.

However, the company has a limited infrastructure budget and data engineering capacity. Purchasing a separate warehouse immediately could introduce additional costs before the reporting requirements and data volumes have been properly assessed.

The 12-month roadmap therefore prioritises the read replica and Python ETL pipeline in Q1, requirements assessment in Q3 and warehouse implementation in Q4.

## Decision

Adopt PostgreSQL as Kloud Kart's dedicated data warehouse platform, with procurement and implementation planned for Q4.

During Q1 and Q2, the Data Engineer will establish the MySQL read replica and automate Python-based data extraction, cleaning, validation and transformation.

During Q3, the company will assess storage requirements, reporting workloads, historical data needs, hosting costs and Nigeria integration requirements.

In Q4, subject to management approval and the Q3 assessment, PostgreSQL will be configured as the central analytical environment.

The Python ETL pipeline will then load validated historical and new data from the read replica into PostgreSQL. Power BI will connect to the warehouse for consolidated reporting.

The warehouse should be deployed separately where possible. If the approved infrastructure budget requires shared hosting, resource isolation and capacity testing must be completed before production use.

## Alternatives considered

### Alternative A: Continue using only MySQL and the read replica

- **How it would work:** Use the read replica as the permanent reporting database without introducing a dedicated warehouse.
- **Why it is attractive:** It reduces infrastructure expenditure and makes use of existing database skills.
- **Why rejected:** As the business grows and expands into Nigeria, historical reporting and consolidated analysis may become more demanding. The replica is primarily intended to protect production and support extraction, not become the permanent analytical platform.

### Alternative B: Adopt a data lake or lakehouse

- **How it would work:** Introduce a platform designed to store large volumes of raw and structured data or combine lake and warehouse capabilities.
- **Why it is attractive:** It offers flexibility for different data formats and more advanced analytical workloads.
- **Why rejected:** Kloud Kart's current requirements are primarily structured business reporting. A lake or lakehouse would introduce additional complexity that the current team and budget do not justify.

### Alternative C: Purchase Snowflake or BigQuery immediately

- **How it would work:** Use a managed cloud data warehouse for analytical storage and processing.
- **Why it is attractive:** These platforms offer managed infrastructure and scaling capabilities.
- **Why rejected:** Their recurring costs and additional platform requirements are not necessary for the company's immediate needs.

### Alternative D: Introduce PostgreSQL in Q4

- **How it would work:** Establish the reporting pipeline first, assess actual requirements in Q3 and deploy PostgreSQL in Q4.
- **Why it is attractive:** It balances long-term analytical requirements with current financial and technical constraints.
- **Why selected:** PostgreSQL provides structured analytical storage using technology that is accessible to the proposed technical team. Delaying procurement also gives management better evidence for its investment.

## Consequences

- **What this buys:** A dedicated environment for historical reporting, consolidated Ghana and Nigeria analysis, consistent business metrics and future analytical development.
- **What this costs:** Warehouse hosting, storage, migration, configuration, backup, monitoring and maintenance. The Data Engineer will also need to manage ETL integration and data validation.
- **What it costs the client if I am wrong:** If the warehouse is introduced before the business needs it, the company may incur unnecessary costs. If procurement is delayed beyond Q4 despite capacity problems, reporting performance and expansion analysis may suffer.
- **What would make me revisit this:** Q3 capacity assessment results, significant increases in data volume, additional reporting requirements or hosting costs that make another platform more suitable.

## What this survives

This decision survives pressure to purchase a sophisticated cloud analytics platform simply because Kloud Kart is expanding.

The business needs a reliable analytical environment, but the implementation should reflect its current resources.

PostgreSQL is the recommended long-term warehouse. The Q4 procurement timeline allows the company to establish its data pipeline, assess actual requirements and make a more informed investment.

The warehouse should be operational by the end of Q4, subject to the Q3 capacity and cost review.