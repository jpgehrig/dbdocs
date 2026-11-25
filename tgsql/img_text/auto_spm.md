#

The graphic depicts the workflow of SPM Evolve Advisor:

1.  Checks AWR for top SQL

    AWR stores the most resource-intensive SQL statements. AWR guides SPM Evolve Advisor, allowing it to identify plans that are most likely to benefit from SQL plan baselines. The overall goal is to prevent plan performance regressions.

2.  Looks for alternate plans in all available sources

    By default, the automatic task searches the shared SQL area, AWR repository, and SQL tuning sets for plans that are not yet in the SMB plan history.

3.  Adds unaccepted plans to plan history

    These plans are not yet in the SQL plan baseline for any statement.

4.  Performs test executions of as many plans as possible during the maintenance window

    For each alternate plan, the database test executes the statement and records the performance statistics. The goal is to use a cost-based algorithm to compare the performance of each current plan to each alternate plan.

5.  Depending on whether the alternative plan performs better then the current plan, SPM Evolve Advisor does the following:

    - If better, then SPM Evolve Advisor accepts the plan. The alternate plan is now in the baseline.

    - If worse, then SPM Evolve Advisor does not add the plan to the baseline. The plan remains in the statement history only.
