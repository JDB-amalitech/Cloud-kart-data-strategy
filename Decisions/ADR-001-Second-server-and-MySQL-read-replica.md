# ADR-001: Separate reporting workloads using a second server and MySQL read replica

- **Status:** Proposed (for client review)
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart leadership, with the Data Engineer responsible for implementation.

## Context

Kloud Kart operates its website, orders, inventory and customer accounts on a single MySQL production server. The database is approximately 40 GB and supports around 4,000 orders daily.

Reporting exports and analytical queries have slowed down the live website twice in the past month. This indicates that the current arrangement exposes customer-facing operations to unnecessary reporting workloads.

The company has already approved a second server and has limited resources for implementing a new data environment.

The immediate priority is to protect the production database while establishing a reliable foundation for automated reporting.

## Decision

Use the approved second server to host a MySQL read replica of the production database.

The read replica will receive replicated changes from production and serve as the source for reporting extraction and analytical queries.

Python ETL processes will extract, clean, validate and prepare reporting datasets from the replica. Power BI will initially consume these prepared datasets without running heavy analytical queries against production.

The second server may also host ETL processing during the initial phase, subject to resource and capacity testing.

The Data Engineer will configure replication monitoring, backup arrangements and alerts for replication delays and failed processes.

## Alternatives considered

### Alternative A: Continue running reporting queries on production

- **How it would work:** Continue using the existing MySQL server for customer transactions and management reporting.
- **Why it is attractive:** It avoids additional infrastructure and implementation costs.
- **Why rejected:** Reporting activities have already caused two website slowdowns. Continuing this approach exposes the company to further performance problems.

### Alternative B: Introduce a second server with a MySQL read replica

- **How it would work:** Replicate production data to the second server and use it for reporting extraction and analytical processing.
- **Why it is attractive:** It separates reporting workloads from live transactions while making use of already approved infrastructure.
- **Why selected:** It directly addresses the existing performance problem and provides a practical first step towards the proposed data warehouse architecture.

### Alternative C: Move all reporting directly into a PostgreSQL warehouse immediately

- **How it would work:** Procure and configure PostgreSQL as a dedicated reporting environment immediately.
- **Why it is attractive:** It provides a separate analytical database and supports historical reporting.
- **Why rejected:** Although PostgreSQL is the recommended long-term solution, immediate procurement would increase initial expenditure before the company has established the reporting pipeline and assessed its actual capacity requirements.

## Consequences

- **What this buys:** Reduced reporting pressure on production, improved website reliability and a separate environment for analytical extraction.
- **What this costs:** Additional server hosting, storage, backup, monitoring and maintenance. The Data Engineer must also manage replication and resource utilisation.
- **What it costs the client if I am wrong:** If the second server cannot handle replication and ETL workloads together, additional infrastructure may be needed. If replication delays are not detected, reporting datasets may contain outdated information.
- **What would make me revisit this:** Persistent replication delays, insufficient server capacity, reporting performance problems or increased workload during Nigeria's expansion.

## What this survives

This decision survives pressure to build the entire analytical platform immediately.
The company has a confirmed production performance problem and an approved second server. Separating reporting workloads is the most direct intervention.
The read replica is an initial reporting solution, not a replacement for the planned PostgreSQL data warehouse in Q4.