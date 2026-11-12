1. Situation Diagnosis – Kloud Kart

1.1 Executive diagnosis
Kloud Kart does not primarily have a dashboard problem. It has a data management and reliability problem.
The company collects enough information to support better business decisions, but that information is scattered across operational processes, extracted manually and interpreted differently by different departments.

The biggest concern is that the same database responsible for serving customers is also being used to produce management reports.

1.2 Root causes, business impact and risk ranking
1.2 Root causes, business impact and risk ranking
1 – Critical
 Production database is doing two jobs

Root cause: The live MySQL database handles two different workloads:
- Running the online shop (customer orders, payments and inventory).
- Producing large reports through CSV exports and database queries.
These workloads compete for the same computer resources, including memory, processing power and disk activity.
How the problem happens
One shared server

MySQL database + live website

Customer orders

Needs fast responses


Monday exports

Uses significant resources



Resource competition
Website becomes slow


Short scenario: Imagine 100 customers are shopping while Nana runs a report containing hundreds of thousands of rows. Both activities compete for the same server resources. The report may slow down customer checkout.

Business cost:
- Lost sales when customers abandon slow checkouts.
- Poor customer experience and reduced trust.
- Potential revenue loss during reporting periods