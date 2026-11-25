This example targets customers in Brazil for a special promotion that offers coupons and an affinity card.

The query uses data on marital status, education, and income to predict the customers who are most likely to take advantage of the incentives. The query applies a decision tree model called `dt_sh_clas_sample` to score the customer data.

Example 1-1 Predict Best Candidates for an Affinity Card

    SELECT cust_id
      FROM mining_data_apply_v
      WHERE
          PREDICTION(dt_sh_clas_sample
                       USING cust_marital_status, education, cust_income_level ) = 1
      AND country_name IN 'Brazil';

      CUST_ID
    ----------
        100404
        100607
        101113

The same query, but with a bias to favor false positives over false negatives, is shown here.

    SELECT cust_id
      FROM mining_data_apply_v
      WHERE
          PREDICTION(dt_sh_clas_sample COST MODEL
                       USING cust_marital_status, education, cust_income_level ) = 1
      AND country_name IN 'Brazil';

      CUST_ID
    ----------
        100139
        100163
        100275
        100404
        100607
        101113
        101170
        101463

The `COST MODEL` keywords cause the cost matrix associated with the model to be used in making the prediction. The cost matrix, stored in a table called `dt_sh_sample_costs`, specifies that a false negative is eight times more costly than a false positive. Overlooking a likely candidate for the promotion is far more costly than including an unlikely candidate.

    SELECT * FROM dt_sh_sample_cost;

    ACTUAL_TARGET_VALUE PREDICTED_TARGET_VALUE       COST
    ------------------- ---------------------- ----------
                      0                      0          0
                      0                      1          1
                      1                      0          8
                      1                      1          0
