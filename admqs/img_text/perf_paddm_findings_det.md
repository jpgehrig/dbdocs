This screenshot shows the Performance Finding Details page. The time the page was last refreshed appears at the top right of the page.

The following fields and values appear at the top of the page:

- Finding: SQL statements consuming significant database time were found. These statements offer a good opportunity for performance improvements.

- Impact (Active Sessions): 3.88

- Percentage of Finding's Impact (%): 89%

- Period Start Time: Thu, Sep 27, 2012 9:00:18 AM

- End Time: Thu, Sep 27, 2012 10:00:03 AM

A findings table appears at the bottom of the page with the first row selected, and with these columns and values:

- Category: SQL Tuning

- Actions: Run SQL Tuning Advisor on the SELECT statement with SQL ID "4fu6qr2958r3m".

- Rationales:

  - The SQL spent 90% of its database time on CPU, I/O and Cluster waits. This part of database time may be improved by the SQL Tuning Advisor.

  - Database time for this SQL was divided as follows: 77% for SQL execution, 0% for parsing, 23% for PL/SQL execution, and 0% for Java execution.

  - SQL statement with SQL ID "4fu6qr2958r3m" was executed 85 times and had an average elapsed time of 22 seconds.

  - At least one execution of the statement ran in parallel.

  - At least two distinct execution plans were utilized for this SQL statement during the analysis period.

- Benefit (%): 11.2%

Just above the findings table, the Implement button is available for the selected finding.
