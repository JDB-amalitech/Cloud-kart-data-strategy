# ADR-003: Adopt daily batch processing and incremental Python ETL for business reporting

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Proposed: Kloud Kart leadership, with the Data Engineer responsible for implementation.

## Context

Kloud Kart needs automated reporting for sales, revenue, customer activity, product performance and regional operations.

The company has requested better business visibility, but its requirements do not establish a need for second-by-second analytics across all departments.

The business permits daily updates for general reporting, while stock availability must remain current.

The company also has limited data engineering capacity and needs a processing approach that can be maintained without introducing unnecessary operational complexity.

## Decision

Adopt scheduled daily batch processing using Python ETL pipelines.

The pipeline will extract data from the MySQL read replica, clean and transform records, validate data quality and prepare reporting datasets.

Incremental extraction will be used to process new and changed records rather than copying the entire production database every day.

The processing schedule will support:

- Daily sales and revenue reporting.
- Daily customer and marketing analysis.
- Daily product and regional performance reporting.
- Historical data preparation for the PostgreSQL warehouse in Q4.

The pipeline must include duplicate checks, missing-value checks, invalid transaction checks and comparisons between source and reporting totals.

Failed jobs and replication delays must generate alerts for the responsible Data Engineer.

Stock availability will remain an immediate operational process using the primary MySQL database.

## Alternatives considered

### Alternative A: Real-time streaming for all business data

- **How it would work:** Continuously process every order, payment, customer event and other business transaction.
- **Why it is attractive:** It provides near-immediate reporting information.
- **Why rejected:** The current requirements do not justify the infrastructure and monitoring complexity of continuous processing across all business functions.

### Alternative B: Full database extraction every day

- **How it would work:** Copy and process the complete production dataset for every reporting run.
- **Why it is attractive:** It is relatively straightforward to understand and implement initially.
- **Why rejected:** Repeated full extraction can waste processing resources as data volumes increase. It also makes the reporting process less efficient over time.

### Alternative C: Daily incremental batch processing

- **How it would work:** Extract new and changed records from the read replica on a schedule and process them using Python.
- **Why it is attractive:** It reduces unnecessary processing and provides predictable reporting updates.
- **Why selected:** It is suitable for the company's daily reporting requirements and can be maintained by a small technical team.

## Consequences

- **What this buys:** Automated reporting, predictable processing schedules, reduced unnecessary extraction and easier monitoring.
- **What this costs:** The Data Engineer must maintain ETL scripts, extraction checkpoints, validation rules, logs and failure alerts. Management must also accept that general reports are not continuously updated.
- **What it costs the client if I am wrong:** Daily reporting may delay decisions if a business function requires more frequent information. Incorrect incremental extraction logic may also omit or duplicate changed records.
- **What would make me revisit this:** Evidence that daily reporting creates financial or operational losses, or a specific business requirement for faster information, such as fraud monitoring or payment monitoring.

## What this survives

This decision survives pressure to make every business dashboard real time.

The objective is not to process data as frequently as possible. It is to provide accurate information at the frequency required by the business.

Daily batch processing is appropriate for general reporting, while genuinely time-sensitive operational requirements can be addressed separately.