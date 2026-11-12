# 1. Situation Diagnosis – Kloud Kart

## 1.1 Executive Diagnosis

Kloud Kart does not primarily have a dashboard problem. It has a **data management and reliability problem**.

The company collects enough information to support better business decisions, but that information is scattered across operational processes, extracted manually and interpreted differently by different departments.

The biggest concern is that the same database responsible for serving customers is also being used to produce management reports.

This creates risks around website performance, customer data protection, reporting accuracy and inventory management.

## 1.2 Root Causes, Business Impact and Risk Ranking

### 1. Production Database Is Doing Two Jobs

**Risk level: Critical**

**Root cause**

The live MySQL database handles two different workloads:

- Running the online shop (customer orders, payments and inventory).
- Producing large reports through CSV exports and database queries.

These workloads compete for the same server resources, including memory, processing power and disk activity.

**Short scenario**

Imagine 100 customers are shopping while Nana runs a report containing hundreds of thousands of rows. Both activities compete for the same server resources. The report may slow down customer checkout.

**Business impact**

- Lost sales when customers abandon slow checkouts.
- Poor customer experience and reduced trust.
- Potential revenue loss during reporting periods.

**Consultant's position**

Separate reporting activities from the live production workload. Introduce a read replica so reporting queries do not compete directly with customer-facing transactions.

### 2. Uncontrolled Customer Data and Privacy Exposure

**Risk level: High – Data Protection**

**Root cause**

Marketing exports approximately 300,000 customer records, but the company does not track where copies are stored, who has access to them or whether old copies are deleted.

The problem is not simply exporting customer information. The problem is losing control of that information after export.

**Short scenario**

A customer requests deletion of their account. Kloud Kart deletes the customer from its main database, but an old marketing spreadsheet still contains their name, email and phone number.

The company may struggle to establish whether all relevant copies have been handled.

**Business impact**

- Exposure to complaints and regulatory action under Ghana's Data Protection Act, 2012 (Act 843).
- Loss of customer trust.
- Time and legal costs investigating complaints.
- Difficulty demonstrating that deletion requests have been properly handled.

**Cost measurement**

The 300,000-person marketing list represents the known exposure population, not the number of affected customers or evidence of a data breach.

A useful financial estimate is:

`Investigation hours × Staff hourly cost + Legal/advisory cost + Remediation cost`

The company also has only 90 days to respond to the stated Data Protection Commission complaint.

**Consultant's position**

Introduce:

- Controlled access to customer information.
- Export tracking to record who exports data, when and why.
- A deletion register.
- Documented procedures for processing deletion requests across approved systems and copies.

### 3. No Single Trusted Version of Business Figures

**Risk level: High – Reporting Reliability**

**Root cause**

Nana and Finance independently export, filter and calculate figures using different spreadsheets and possibly different definitions.

For example, they may count:

- Orders placed versus orders successfully paid.
- Cancelled orders versus completed orders.
- Gross sales versus net sales.
- Orders created on different dates or time zones.

**Business impact**

- Management makes decisions using inconsistent figures.
- Meetings are wasted reconciling spreadsheets.
- Investors may question the reliability of the company's financial and operational reporting.

**Cost measurement**

If two employees each spend four hours reconciling reports every week, the business loses:

`2 employees × 4 hours × 52 weeks = 416 working hours annually`

**Consultant's position**

Establish one agreed definition for every important business measure, such as:

- Total orders.
- Completed orders.
- Revenue.
- Cancelled orders.

Both departments must use the same approved calculations when producing reports.

### 4. Inventory Accuracy and Overselling Risk

**Risk level: High – Operational Reliability**

**Root cause**

Kloud Kart's inventory information is held in its operational database, but reporting and other copied data may not reflect the latest stock movements.

Unlike management reports, stock information cannot wait until the next day. A delayed stock update can result in a product being sold when it is no longer available.

**Short scenario**

A customer buys the last phone. Before the inventory report updates, another customer sees that the phone is available and places an order.

Kloud Kart now has two customers expecting one phone.

**Business impact**

- Refunds and order cancellations.
- Customer complaints.
- Extra delivery and customer service costs.
- Loss of customer confidence.

**Cost measurement**

If 10 orders per day are affected and each requires GH₵30 in additional handling or recovery costs:

`10 orders × GH₵30 × 30 days = GH₵9,000 monthly exposure`

This is an illustrative scenario, not a confirmed Kloud Kart loss.

**Consultant's position**

- Keep stock updates within the live operational system.
- Ensure the reporting system reads stock information without becoming a separate authority for stock availability.
- Stock changes must be reflected immediately in the operational system, not through daily reporting refreshes.

## 1.3 Overall Risk Ranking for the Board

The ranking considers business continuity, financial exposure, regulatory exposure and the company's ability to support expansion.

| Rank | Root Cause | Main Business Risk | Priority |
|---:|---|---|---|
| 1 | Shared production database | Website performance problems and potential lost sales | Critical |
| 2 | Uncontrolled customer data | Regulatory and privacy exposure | High |
| 3 | Inconsistent business reporting | Poor investor and management decisions | High |
| 4 | Inventory accuracy risk | Overselling and customer dissatisfaction | High |

**Overall conclusion**

Kloud Kart needs to establish a reliable and controlled data management environment before expanding its reporting capabilities.

The immediate priority is to protect the live production database, improve customer data governance, standardise business reporting and preserve real-time inventory accuracy.

These improvements will provide a stronger foundation for the company's expansion into Nigeria.