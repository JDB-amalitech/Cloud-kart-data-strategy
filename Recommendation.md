# 2. Recommendation – Kloud Kart Data Strategy
## 2.1 Executive recommendation

Kloud Kart should adopt a **PostgreSQL data warehouse**, supported by a MySQL read replica and automated Python ETL pipelines. The read replica and Python ETL come first (Q1); the warehouse is introduced in Q4, subject to the Q3 capacity and cost review.

The purpose is to separate business reporting from the live website, establish one trusted source of business information and prepare the company for expansion into Nigeria.

Rather than purchasing expensive platforms such as Snowflake or BigQuery immediately, Kloud Kart should use PostgreSQL, Python and Power BI. These technologies provide the required capabilities at a more manageable cost.

## 2.2 Proposed architecture

The proposed data flow is:

**MySQL Production → MySQL Read Replica → Python ETL Pipeline → PostgreSQL Data Warehouse → Power BI**

| Component | Responsibility |
|---|---|
| MySQL Production | Handles live website operations, orders, payments, customers and inventory. |
| MySQL Read Replica | Receives a copy of production data and provides a separate source for reporting extraction. |
| Python ETL Pipeline | Automatically extracts, cleans, validates and transforms data. |
| PostgreSQL Data Warehouse (introduced in Q4) | Stores organised historical data for business analysis across Ghana and Nigeria. |
| Power BI | Presents sales, finance, customer and regional performance dashboards. |

The warehouse will organise information into reporting-friendly tables, including sales, products, customers, dates and locations. This will allow management to compare business performance across both countries.

**Important inventory decision:** Stock availability must always be checked against the primary MySQL database. The warehouse and read replica must not be used to approve purchases because their data may be delayed.

The second server can initially host the read replica and ETL processing, with the warehouse deployed separately where possible. If the approved infrastructure budget requires them to share a server, resource isolation and capacity testing must be completed before production use.

## 2.3 Why choose a data warehouse?

| Option | Advantages | Decision |
|---|---|---|
| Data warehouse | Organises historical business data and supports consistent reporting and analysis. | **Selected** – introduced in Q4, after the Q3 review. |
| Data lake | Stores large amounts of raw data in different formats. | Defer; current needs are mainly structured business data. |
| Lakehouse | Combines data lake and warehouse capabilities. | Defer; additional complexity is not justified by the current team and requirements. |
| Snowflake / BigQuery | Managed cloud warehouse services with strong scaling capabilities. | Reconsider when growth and workloads justify their recurring costs. |

A PostgreSQL data warehouse gives Kloud Kart a structured reporting environment without introducing the cost and operational demands of a more advanced cloud platform.

## 2.4 Processing approach

Kloud Kart should adopt **daily batch processing**, rather than building a full real-time analytics platform.

| Data activity | Processing frequency | Reason |
|---|---|---|
| Sales and revenue reports | Daily | Suitable for management and finance reporting. |
| Customer and marketing analysis | Daily | Provides updated customer trends without repeated manual exports. |
| Product and regional performance | Daily | Supports comparisons between Ghana and Nigeria. |
| Stock availability | Immediate, through primary MySQL | Prevents overselling and stale stock decisions. |

The Python pipeline will use incremental extraction to process new and changed records rather than copying the entire database every day. It will also check for duplicate records, missing values, invalid transactions and differences between source and warehouse totals.

Failed jobs and replication delays must generate alerts for the responsible data engineer.

**Why not real-time dashboards?** Kloud Kart has not identified a business requirement that needs every sales transaction displayed within seconds. Daily reporting is sufficient for the current management and finance needs. Real-time processing can be considered later for specific requirements such as fraud detection or payment monitoring.

## 2.5 Data protection and reliability

The company should implement:

1. Role-based access so employees only see information required for their jobs.
2. Encryption for data transfers and stored customer information.
3. Export logs showing who accessed or downloaded customer lists.
4. A deletion register to track customer deletion requests across production, replicas, the warehouse and marketing exports.
5. A documented data-retention policy that considers legal obligations.
6. Regular backups and tested recovery procedures.

For the existing Data Protection Commission complaint, Kloud Kart must investigate all relevant data locations, document the actions taken and respond within the stated 90-day period. Removing a customer record from production MySQL alone does not prove that all copies have been addressed.

The company should obtain appropriate data-protection advice to confirm its obligations under Ghana's Data Protection Act, 2012 (Act 843), including requirements relevant to its Nigeria operations.

## 2.6 Final recommendation

Kloud Kart should invest in a PostgreSQL data warehouse supported by a MySQL read replica, automated Python ETL pipelines and Power BI.

This architecture separates analytical reporting from the live website, gives Finance and Operations a consistent source of business figures, and supports comparisons between Ghana and Nigeria.

The company should not spend on a lakehouse, full real-time dashboards, machine learning or expensive cloud warehouse subscriptions yet. These are future options, not immediate requirements.

The priority is to build a reliable data foundation that fits Kloud Kart's current size, protects its operations and can grow with the business.