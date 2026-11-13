# 3. 12-Month Implementation Roadmap – Kloud Kart

**Objective:** Protect customer information, remove reporting pressure from the live website, establish reliable business reporting and prepare the company for Nigeria's expansion.

The implementation will be phased to control costs. Kloud Kart will initially use a MySQL read replica and automated Python processing. The PostgreSQL data warehouse will be introduced in Quarter 4, when the Nigeria pilot creates a stronger need for consolidated reporting across both countries.

| Period | Key activities and priorities | Outcomes Nana can personally verify |
|---|---|---|
| **Q1: Months 1–3 – Protect and stabilise** | **Hire 1: Data Engineer (Month 1).** Set up the MySQL read replica and automate daily Python extraction and processing. Prepare controlled reporting datasets for Power BI using imported data rather than heavy queries against production. Introduce access controls, export tracking, retention rules and a customer deletion register. Investigate the existing Data Protection Commission complaint and obtain appropriate privacy/legal support. | 1. Monday reports can be produced without manually exporting data from the live website database. 2. Reporting runs no longer slow the live website. 3. Finance and Operations use agreed definitions for orders and revenue. 4. The existing deletion complaint has been investigated, documented and responded to within the stated 90-day deadline. 5. Customer-data exports and access can be traced to authorised employees. |
| **Q2: Months 4–6 – Improve reporting and accountability** | **Hire 2: Data Analyst/BI Developer (Month 4).** Improve report definitions, validate figures, develop Power BI dashboards and establish regular data-quality checks. Review customer-data access, deletion requests and backup procedures. | 1. Nana and Finance can open the same dashboard and see matching sales and revenue figures. 2. Nana can check daily orders, cancellations and top-selling products without asking the developer for manual reports. 3. Customer-data exports have identifiable owners and documented purposes. 4. Deletion requests have documented progress and completion evidence. 5. Management can confirm that backups and recovery procedures have been tested. |
| **Q3: Months 7–9 – Prepare for Nigeria** | Extend reporting to include Nigeria's pilot operations. Agree on common definitions for orders, revenue, products and customers across both countries. Review data quality, reporting volume, storage needs and infrastructure capacity. Design the PostgreSQL warehouse structure and assess supplier and hosting costs before purchase. | 1. Nana can distinguish Ghana and Nigeria transactions in the reports. 2. Management can compare sales and order volumes by country. 3. Both countries use consistent reporting definitions. 4. The company has a documented warehouse design, capacity assessment and cost proposal ready for approval. 5. Customer-data handling and cross-border processing arrangements have been reviewed with appropriate privacy advice. |
| **Q4: Months 10–12 – Introduce the data warehouse** | Purchase and configure the PostgreSQL data warehouse infrastructure. Connect the Python ETL pipeline to load validated historical and new data from the read replica. Connect Power BI to the warehouse. Test performance, security, backup, recovery and deletion procedures. Assess readiness for future demand forecasting. | 1. Nana can view Ghana and Nigeria performance from one central reporting environment. 2. Finance and Operations use the same trusted reports. 3. Reports no longer depend on manual spreadsheet consolidation. 4. Management can verify that the warehouse is backed up, secured and operating reliably. 5. The board receives a year-end report on reporting improvements, costs, risks and whether demand forecasting is now justified. |

## End-of-year success measures

| Area | Expected result after 12 months |
|---|---|
| Website reliability | Reporting activity is separated from the production database. |
| Management reporting | Agreed reports are automated and available daily. |
| Reporting consistency | Finance and Operations use the same business definitions. |
| Data protection | Customer access, exports, retention and deletion are controlled and documented. |
| Inventory | Live stock decisions continue to use the primary MySQL database. |
| Nigeria expansion | Ghana and Nigeria performance can be compared consistently. |
| Data warehouse | PostgreSQL warehouse is operational by the end of Q4, subject to the Q3 capacity and cost review. |
| Future analytics | Management has evidence to decide whether demand forecasting is worth investing in. |

**Management accountability:** At the end of each quarter, Nana should verify the outcomes using dashboards, reports, export records, deletion records and system test results. A technical task is not complete simply because the Data Engineer says it has been deployed.

**Hiring sequence:** The Data Engineer joins in Month 1 because the company first needs to protect the live database, establish automated extraction and address data reliability. The Data Analyst/BI Developer joins in Month 4 to turn the processed data into trusted business reports and dashboards. Privacy accountability remains with management, supported by appropriate legal or data-protection advice; it should not be left solely to the two technical hires.