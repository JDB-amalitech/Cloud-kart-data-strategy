# **Developer Improvement Plan – Kloud Kart**

**Duration:** 12 Months\
**Position:** Existing PHP/MySQL Developer\
**Objective:** Improve the developer's technical skills, strengthen the reliability of Kloud Kart's application and support the proposed data architecture without creating an additional permanent position.

## **1. Improvement objectives**

The developer should focus on six key areas:

1. **PHP development:** Improve code quality, error handling, application maintenance and testing.
2. **MySQL management:** Improve SQL queries, indexing, database performance and transaction management.
3. **Database security:** Apply access controls, secure credentials and support customer-data protection.
4. **Reporting support:** Ensure operational records are accurate and available for automated reporting.
5. **System integration:** Support the Data Engineer with read replica and warehouse integration.
6. **Documentation:** Maintain database structures, application workflows and technical changes.

## **2. Twelve-month improvement roadmap**

| Period                                       | Key activities                                                                                                                                           | Expected deliverables                                                                              |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Q1: Stabilisation (Months 1–3)**           | Review PHP application and MySQL queries. Identify performance issues. Support read replica implementation. Improve database security and documentation. | Application assessment, optimised queries, database documentation and improved access controls.    |
| **Q2: Reporting improvement (Months 4–6)**   | Support Monday reporting reconciliation. Investigate missing, duplicate or inconsistent orders and payments. Improve transaction handling.               | Documented reconciliation issues, improved order/payment processes and reporting data definitions. |
| **Q3: Nigeria preparation (Months 7–9)**     | Support country-specific application configuration. Test order, payment and inventory workflows for the Nigerian pilot.                                  | Application readiness assessment and integration test results.                                     |
| **Q4: Warehouse integration (Months 10–12)** | Support PostgreSQL warehouse integration. Validate source records against reporting outputs. Participate in backup and recovery tests.                   | Integration test results, reconciliation evidence and technical improvement report.                |

## **3. Monday reporting and reconciliation responsibilities**

The developer must support the accuracy of operational data used for Monday management reports.

| Area                      | Developer's responsibility                                                |
| ------------------------- | ------------------------------------------------------------------------- |
| Orders                    | Check missing, duplicate and incorrectly recorded orders.                 |
| Payments                  | Investigate payment discrepancies.                                        |
| Cancellations and refunds | Ensure transactions are correctly recorded.                               |
| Revenue                   | Help investigate differences between source records and reported figures. |
| Inventory                 | Maintain accurate stock movements and order updates.                      |
| Data discrepancies        | Investigate technical errors and document corrections.                    |

**Reporting workflow:**

**MySQL Production → MySQL Read Replica → Python ETL and Validation → PostgreSQL Data Warehouse → Power BI Reports**

The developer maintains reliable application records. The Data Engineer manages extraction and warehouse processes, while the Data Analyst/BI Developer manages reporting definitions and dashboards.

## **4. Required technical development**

| Skill             | Improvement focus                                                                            |
| ----------------- | -------------------------------------------------------------------------------------------- |
| PHP               | Secure coding, error handling and testing.                                                   |
| MySQL/SQL         | JOINs, indexing, query optimisation and transactions.                                        |
| Database security | Access permissions and credential management.                                                |
| Git/GitHub        | Version control and code reviews.                                                            |
| API integration   | Application and payment-system integration.                                                  |
| Python/PostgreSQL | Understand ETL and warehouse integration sufficiently to collaborate with the Data Engineer. |

## **5. Performance indicators**

Management should evaluate the developer using measurable evidence.

- Routine reporting no longer places heavy workloads on production MySQL.
- Critical application and database documentation is completed.
- Order, payment and inventory records are reliable.
- Monday reporting discrepancies are investigated and documented.
- Database access permissions are reviewed.
- Application testing for Nigeria is completed before expansion.
- Warehouse integration and reconciliation tests are supported in Q4.
- Backup and recovery procedures are tested.

## **6. Roles and accountability**

| Role                                | Main responsibility                                                                          |
| ----------------------------------- | -------------------------------------------------------------------------------------------- |
| Existing Developer                  | PHP application, production MySQL, order and inventory reliability, application integration. |
| Data Engineer (Month 1)             | Read replica, Python ETL, PostgreSQL warehouse and data pipelines.                           |
| Data Analyst/BI Developer (Month 4) | Monday reporting, reconciliation definitions, Power BI dashboards and reporting validation.  |
| Management                          | Oversight, resource approval and data protection accountability.                             |

## **7. Expected outcome**

By the end of 12 months, the developer should be able to maintain a secure and reliable application, support accurate Monday reporting, protect operational database performance and collaborate effectively with the two new data hires.

**Recommendation:** Retain and develop the existing PHP/MySQL developer. Keep their responsibilities focused on application reliability and operational database support rather than assigning them full Data Engineering or Business Intelligence responsibilities. This supports the company's two-hire plan while strengthening its existing technical capacity.