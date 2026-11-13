# ADR-004: Keep customer-facing stock availability on the primary MySQL database

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Proposed: Kloud Kart leadership, with the existing PHP/MySQL developer responsible for website integration.

## Context

Kloud Kart requires accurate stock availability when customers place orders.

The proposed architecture introduces a MySQL read replica for reporting and a PostgreSQL data warehouse for historical and analytical information.

Both environments may experience delays between an operational transaction and the availability of that information in reporting datasets.

Using delayed information to approve customer purchases could result in overselling, inaccurate stock availability and poor customer experiences.

The company must therefore distinguish operational inventory decisions from analytical reporting.

## Decision

Keep customer-facing stock availability and purchase validation connected to the primary operational MySQL database.

The existing PHP/MySQL application will continue checking and updating inventory as part of the order transaction process.

The read replica and PostgreSQL warehouse may be used for product performance, historical stock analysis and management reporting, but not to approve purchases or determine live stock availability.

The existing developer must ensure that inventory updates and order confirmation are handled with appropriate database transaction controls.

## Alternatives considered

### Alternative A: Use daily reporting datasets for stock availability

- **How it would work:** The website checks the latest daily reporting dataset before confirming purchases.
- **Why it is attractive:** It would allow stock information to be accessed alongside other reporting data.
- **Why rejected:** Stock could change after the dataset is prepared, creating the risk of selling unavailable products.

### Alternative B: Use the MySQL read replica for stock availability

- **How it would work:** The website reads stock quantities from the replica instead of the primary database.
- **Why it is attractive:** It could reduce some read traffic against production.
- **Why rejected:** Replication lag may cause outdated inventory information to be displayed to customers.

### Alternative C: Retain live stock checks on primary MySQL

- **How it would work:** The website continues validating and updating inventory through the primary operational database.
- **Why it is attractive:** Inventory decisions use the current operational records and remain part of the order transaction process.
- **Why selected:** It satisfies the requirement that stock availability must not become stale.

## Consequences

- **What this buys:** More reliable customer-facing inventory information, reduced risk of overselling and separation between operational and analytical responsibilities.
- **What this costs:** Stock-related reads and updates remain on production. The developer must ensure efficient inventory queries and correct transaction handling.
- **What it costs the client if I am wrong:** Production may continue experiencing pressure from inventory activity. If inventory records or transaction logic are incorrect, customers may still see inaccurate stock information.
- **What would make me revisit this:** Evidence that a separately designed inventory service can guarantee current availability and preserve transaction integrity without introducing unacceptable complexity.

## What this survives

This decision survives pressure to move every data activity away from production.

The read replica and warehouse are designed to support reporting, not replace the operational database.

Accurate stock availability directly affects customer purchases and must remain an operational priority.