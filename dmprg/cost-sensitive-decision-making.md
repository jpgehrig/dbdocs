Costs are user-specified numbers that bias Classification. The algorithm uses positive numbers to penalize more expensive outcomes over less expensive outcomes. Higher numbers indicate higher costs.

The algorithm uses negative numbers to favor more beneficial outcomes over less beneficial outcomes. Lower negative numbers indicate higher benefits.

All classification algorithms can use costs for scoring. You can specify the costs in a cost matrix table, or you can specify the costs inline when scoring. If you specify costs inline and the model also has an associated cost matrix, only the inline costs are used. The `PREDICTION`, `PREDICTION_SET`, and `PREDICTION_COST` functions support costs.

Only the Decision Tree algorithm can use costs to bias the model build. If you want to create a Decision Tree model with costs, create a cost matrix table and provide its name in the `CLAS_COST_TABLE_NAME` setting for the model. If you specify costs when building the model, the cost matrix used to create the model is used when scoring. If you want to use a different cost matrix table for scoring, first remove the existing cost matrix table then add the new one.

A sample cost matrix table is shown in the following table. The cost matrix specifies costs for a binary target. The matrix indicates that the algorithm must treat a misclassified 0 as twice as costly as a misclassified 1.

Table 6-1 Sample Cost Matrix

| ACTUAL_TARGET_VALUE | PREDICTED_TARGET_VALUE | COST |
|:--------------------|:-----------------------|:-----|
| 0                   | 0                      | 0    |
| 0                   | 1                      | 2    |
| 1                   | 0                      | 1    |
| 1                   | 1                      | 0    |

Example 6-14 Sample Queries With Costs

The table `nbmodel_costs` contains the cost matrix described in Table 6-1.

    SELECT * from nbmodel_costs;

    ACTUAL_TARGET_VALUE PREDICTED_TARGET_VALUE       COST
    ------------------- ---------------------- ----------
                      0                      0          0
                      0                      1          2
                      1                      0          1
                      1                      1          0

The following statement associates the cost matrix with a Naive Bayes model called `nbmodel.`

    BEGIN
      dbms_data_mining.add_cost_matrix('nbmodel', 'nbmodel_costs');
    END;
    /

The following query takes the cost matrix into account when scoring `mining_data_apply_v`. The output is restricted to those rows where a prediction of 1 is less costly then a prediction of 0.

    SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
            FROM mining_data_apply_v
            WHERE PREDICTION (nbmodel COST MODEL
           USING cust_marital_status, education, household_size) = 1
            GROUP BY cust_gender
            ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         25         38
    M        208         43

You can specify costs inline when you invoke the scoring function. If you specify costs inline and the model also has an associated cost matrix, only the inline costs are used. The same query is shown below with different costs specified inline. Instead of the "2" shown in the cost matrix table (Table 6-1), "10" is specified in the inline costs.

    SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
        FROM mining_data_apply_v
        WHERE PREDICTION (nbmodel
                  COST (0,1) values ((0, 10),
                             (1, 0))
                  USING cust_marital_status, education, household_size) = 1
        GROUP BY cust_gender
        ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         74         39
    M        581         43

The same query based on probability instead of costs is shown below.

    SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
            FROM mining_data_apply_v
            WHERE PREDICTION (nbmodel
               USING cust_marital_status, education, household_size) = 1
            GROUP BY cust_gender
            ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         73         39
    M        577         44
