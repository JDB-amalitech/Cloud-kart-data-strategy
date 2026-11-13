**From:** Joseph Danquah Botchway  
**To:** Nana  
**Date:** 12 November 2026  
**Subject:** Improving Kloud Kart's Reporting and Data Management

### 1. What I found

Kloud Kart's main challenge is not simply a lack of dashboards; it is how the company manages and uses its data.

Currently, the website, orders, inventory and customer accounts operate on one MySQL server. Management reporting also relies on this database, and reporting exports have already slowed the website on two occasions.

This creates several risks:
- Reporting activities can affect website performance.
- Manual exports increase the possibility of inconsistent figures and errors.
- Customer-data access, exports, retention and deletion need stronger controls.
- Expansion into Nigeria will increase data management and reporting requirements.

### 2. What I built

I developed a proposed data management and reporting improvement plan covering the next 12 months.

The proposed architecture is:

**MySQL Production → MySQL Read Replica → Python ETL → PostgreSQL Data Warehouse → Power BI**

I also developed:
- A phased 12-month implementation roadmap.
- Six Architecture Decision Records (ADRs) explaining the major technical decisions.
- A developer improvement plan to strengthen the existing PHP/MySQL developer's contribution.
- A proposed reporting reconciliation process to improve the accuracy of Monday management reports.
- Data protection, access control, export tracking and deletion recommendations.

The plan introduces the read replica first and delays PostgreSQL warehouse procurement until Q4, after reviewing the company's actual reporting needs, infrastructure capacity and costs.

### 3. What I recommend

I recommend that Kloud Kart adopts a phased approach rather than investing in several expensive technologies immediately.

1. **Q1 – Stabilise:** Recruit a Data Engineer, configure the read replica, automate reporting extraction and strengthen data access controls.
2. **Q2 – Improve reporting:** Recruit a Data Analyst/BI Developer to improve Monday reporting, reconcile figures and develop Power BI dashboards.
3. **Q3 – Prepare for Nigeria:** Establish consistent reporting definitions for both markets and assess infrastructure, storage, data quality and costs.
4. **Q4 – Establish the warehouse:** Procure and implement PostgreSQL as the central reporting warehouse, subject to the Q3 assessment.

I also recommend keeping live inventory and stock availability checks on the production MySQL database. These operational decisions should not depend on delayed reporting data.

The existing PHP/MySQL developer should be retained and developed, while management maintains responsibility for data protection oversight.

### 4. What I could not stand behind

There are areas where I would not recommend making firm commitments without further investigation:

- **Infrastructure costs:** The actual cost of the second server, PostgreSQL warehouse, hosting and maintenance requires supplier quotations.
- **System capacity:** The proposed architecture requires workload and performance testing before full implementation.
- **Data protection compliance:** The existing complaint and the company's compliance position require proper review and advice from a qualified data protection professional. A register alone does not establish compliance.
- **Nigeria expansion:** Cross-border customer-data processing requirements need legal and regulatory assessment before implementation.
- **Forecasting and advanced analytics:** I would not recommend investing in machine learning or demand forecasting until the company has reliable, well-governed data and a clear business need.

### Closing

My recommendation is to prioritise reliability, reporting accuracy and data protection before investing in advanced analytics.

The proposed approach allows Kloud Kart to address its immediate reporting challenges, make better use of its existing resources and prepare for expansion into Nigeria without committing prematurely to unnecessary infrastructure.

I would appreciate your review and direction on the proposed roadmap, recruitment priorities and implementation approach.

**Joseph Danquah Botchway**