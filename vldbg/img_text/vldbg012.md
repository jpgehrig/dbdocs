# Description of the illustration

This image is similar to the earlier intraoperation example. It simply shows how the parallel execution coordinator has two parallel execution servers handle the task of creating a summary table. The data flows from a table called daily_sales through the parallel execution servers into the creation of the summary table.

The statement is CREATE TABLE summary (C1, AVGC2, SUMC3) PARALLEL (5) AS SELECT C1, AVG(C2), SUM(C3) FROM daily_sales GROUP BY (C1);
