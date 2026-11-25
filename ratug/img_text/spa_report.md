# Description of the illustration spa_report.gif

The SQL Performance Analyzer Task Report: SYS.SPA_GUIDED_WORKFLOW page is shown.

In the summary at the top of the page, the SQL Tuning Set Name is DOCTEST3. The STS Owner is SYS. The Total SQL Statements field shows 450. The SQL Statements With Errors field shows 11. The SQL Trial 1 field shows SQL_TRIAL_1336002531305. The SQL Trial 2 field shows SQL_TRIAL_1336002653572. The Comparison Metric field is Elapsed Time.

Below the summary is the Global Statistics section, which includes two bar charts.

The chart on the left is labeled Projected Workload Elapsed Time. It has a y-axis labeled Elapsed Time (sec). The y-axis values range from 0 to 1,500. The x-axis values are SQL Trial 1 (blue) and SQL Trial 2 (brown). The y-axis value of SQL Trial 1 (blue) is just over 1,000. The y-axis value of SQL Trial 2 (brown) is slightly more than SQL Trial 1. The Improvement Impact is 0%. The Regression Impact is -2%. The Overall Impact is -2%.

The chart on the right is labeled SQL Statement Count. The y-axis is labeled SQL Count and ranges from 0 to 500. The x-axis is labeled Change in Elapsed Time. The x-axis has the following values: Improved, Regressed, and Unchanged. Improved has a y-axis value of 0. Regressed has a y-axis value of 0. The bar for Unchanged is green and has a y-axis value of about 450, which represents Same Plan. There are no bars colored orange, which represents New Plan.

To the right of the SQL Statement Count chart is the Recommendations section. The text in the Recommendations section reads "Oracle offers two options to fix regressed SQL resulting from plan changes: Use the better execution plan from SQL Trial 1 by creating SQL Plan Baselines." Below that text is the Create SQL Plan Baselines button. Below the Create SQL Plan Baselines button is this additional text: "Explore alternate execution plans using SQL Tuning Advisor." Below that text is the Run SQL Tuning Advisor button.

Below the Global Statistics section is the Top 10 SQL Statements Based on Impact on Workload section. The table contains the following columns: null, SQL ID, Net Impact on Workload (%), Elapsed Time (sec) SQL Trial 1, Elapsed Time (sec) SQL Trial 2, Net Impact on SQL (%), New Plan.

End of description.
