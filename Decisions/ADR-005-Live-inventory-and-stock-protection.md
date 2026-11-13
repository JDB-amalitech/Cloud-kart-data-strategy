# ADR-005: Introduce controlled customer-data exports and deletion tracking

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Proposed: Kloud Kart leadership, with the Data Analyst/BI Developer coordinating governance activities and management retaining privacy accountability.

## Context

Kloud Kart maintains customer information for approximately 300,000 customers.

Marketing and other departments use customer information for business activities, but the company does not have sufficient visibility into where exported customer lists are stored, who controls them or how long copies are retained.

The company also needs to investigate an existing Data Protection Commission complaint and respond within the stated 90-day deadline.

The proposed data architecture introduces a read replica, Python ETL processing and a PostgreSQL warehouse. This increases the importance of identifying where customer information is stored and who can access it.

The company must establish appropriate data protection controls before expanding its reporting environment.

## Decision

Introduce a customer-data governance process covering production data, replicated data, warehouse datasets, marketing exports and relevant external processors.

The process will include:

1. A register of approved customer-data exports.
2. Documented business purposes and named owners.
3. Role-based access permissions.
4. Export logs and periodic access reviews.
5. Data-retention and secure disposal procedures.
6. A customer deletion request register.
7. Documented evidence of actions taken across relevant systems and copies.
8. Backup and recovery procedures that account for customer-data retention and deletion requirements.

The existing Data Protection Commission complaint must be investigated, documented and responded to within the stated deadline, with appropriate privacy and legal support.

Management will retain responsibility for privacy accountability. The BI and Data Governance Analyst will coordinate records and controls, while the Data Engineer and existing developer support technical implementation.

## Alternatives considered

### Alternative A: Continue manual customer-data exports

- **How it would work:** Allow departments to export and distribute customer lists without a central register.
- **Why it is attractive:** It is familiar and requires little initial investment.
- **Why rejected:** It does not address the existing lack of visibility and accountability over customer information.

### Alternative B: Purchase a complete customer-data management platform immediately

- **How it would work:** Introduce a central platform for customer information, access and deletion management.
- **Why it is attractive:** It could provide more advanced governance and data management capabilities.
- **Why rejected:** It introduces additional cost and does not automatically address existing spreadsheets, exports and external copies.

### Alternative C: Establish controlled exports and a documented request process

- **How it would work:** Introduce registers, ownership, access controls, retention procedures and documented request tracking.
- **Why it is attractive:** It addresses the immediate control gaps without requiring an expensive new platform.
- **Why selected:** It is manageable within the current implementation plan and creates a foundation for stronger governance as the company expands.

## Consequences

- **What this buys:** Improved visibility of customer information, clearer accountability, traceable exports and better evidence of customer-data request handling.
- **What this costs:** Staff time, documentation, access reviews, secure storage and appropriate privacy advice.
- **What it costs the client if I am wrong:** If employees fail to record exports or external processors are overlooked, the register may be incomplete and create a false sense of security. Inadequate deletion and retention procedures could also create regulatory and customer-trust risks.
- **What would make me revisit this:** Increased data-sharing complexity, additional regulatory requirements, inability to control existing copies or evidence that a more advanced governance platform is required.

## What this survives

This decision survives pressure to solve customer-data protection by simply moving information into one central database.

The immediate problem is insufficient visibility and accountability over customer information.

The company must establish ownership, track exports and document customer-data requests across relevant systems. The process must be reviewed against Ghana's Data Protection Act, 2012 (Act 843), with qualified privacy advice, particularly for cross-border processing involving Nigeria.

Recording a deletion request does not itself establish that all copies have been deleted or that the company is legally compliant.