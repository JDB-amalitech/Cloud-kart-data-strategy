1. Situation Diagnosis – Kloud Kart

1.1 Executive diagnosis
Kloud Kart does not primarily have a dashboard problem. It has a data management and reliability problem.
The company collects enough information to support better business decisions, but that information is scattered across operational processes, extracted manually and interpreted differently by different departments.

The biggest concern is that the same database responsible for serving customers is also being used to produce management reports.

1.2 Root causes, business impact and risk ranking
1.2 Root causes, business impact and risk ranking

1 – Critical -Developmental Landscope
 Production database is doing two jobs

Root cause: The live MySQL database handles two different workloads:
- Running the online shop (customer orders, payments and inventory).
- Producing large reports through CSV exports and database queries.
These workloads compete for the same computer resources, including memory, processing power and disk activity.

Short scenario: Imagine 100 customers are shopping while Nana runs a report containing hundreds of thousands of rows. Both activities compete for the same server resources. The report may slow down customer checkout.

Business cost:
- Lost sales when customers abandon slow checkouts.
- Poor customer experience and reduced trust.
- Potential revenue loss during reporting periods

2 – Higher Data Protection 
 Uncontrolled customer data and privacy exposure

Root cause: Marketing exports approximately 300,000 customer records, but the company does not track where copies are stored, who has access to them or whether old copies are deleted.

The problem is not simply exporting customer information. The problem is losing control of that information after export.

Short scenario: A customer requests deletion of their account. Kloud Kart deletes the customer from its main database, but an old marketing spreadsheet still contains their name, email and phone number. The company may struggle to establish whether all relevant copies have been handled.

Business cost:
- Exposure to complaints and regulatory action under Ghana's Data Protection Act, 2012 (Act 843).
- Loss of customer trust.
- Time and legal costs investigating complaints.
- Difficulty demonstrating that deletion requests have been properly handled.
Cost measurement: The 300,000-person marketing list is the known exposure population, not the number of affected customers or evidence of a breach.

A useful financial estimate is:

Investigation hours × staff hourly cost + legal/advisory cost + remediation cost

The company also has only 90 days to respond to the stated Data Protection Commission complaint.

Consultant's position: Introduce controlled access to customer information, track every export, maintain a deletion register and document how deletion requests are processed across approved systems and copies.

3 – High -Relability
 No single trusted version of business figures

Root cause: Nana and Finance independently export, filter and calculate figures using different spreadsheets and possibly different definitions.

For example, they may count:
- Orders placed versus orders successfully paid.
- Cancelled orders versus completed orders.
- Gross sales versus net sales.
- Orders created on different dates or time zones.
- Business cost:
- Management makes decisions using inconsistent figures.
- Meetings are wasted reconciling spreadsheets.
- Investors may question the reliability of the company's financial and operational reporting.
  
Cost measurement: If two employees each spend four hours reconciling reports every week, the business loses eight working hours weekly, or approximately 416 hours annually.

Consultant's position: Establish one agreed definition for every important business measure, such as total orders, completed orders, revenue and cancelled orders. Both departments must use the same approved calculations.

4 – High
 Inventory accuracy and overselling risk

Root cause: Kloud Kart's inventory information is held in its operational database, but reporting and other copied data may not reflect the latest stock movements.

Unlike management reports, stock information cannot wait until the next day. A delayed stock update can result in a product being sold when it is no longer available.

Short scenario: A customer buys the last phone. Before the inventory report updates, another customer sees that the phone is available and places an order. Kloud Kart now has two customers expecting one phone.

Business cost:
- Refunds and order cancellations.
- Customer complaints.
- Extra delivery and customer service costs.
- Loss of customer confidence.
Cost measurement: If 10 orders per day are affected and each requires GH₵30 in additional handling or recovery costs:

10 × GH₵30 × 30 days = GH₵9,000 monthly exposure.

This is an illustrative scenario, not a confirmed Kloud Kart loss.

Consultant's position: Keep stock updates within the live operational system. Any reporting system must read stock information without becoming a separate authority for stock availability. Stock changes must be reflected immediately, not through daily reporting refreshe

1.3 Overall risk ranking for the board
The ranking considers business continuity, financial exposure, regulatory exposure and the ability to support expansion.

Rank	Root cause	Main business risk	Priority
1	Shared production database	Website downtime and lost sales	Critical
2	Uncontrolled customer data	Regulatory and privacy exposure	High
3	Inconsistent business reporting	Poor investor and management decisions	High
4	Inventory accuracy risk	Overselling and customer dissatisfaction	High
5	Lack of data ownership and skills	Operational dependency and slow growth	Medium–High