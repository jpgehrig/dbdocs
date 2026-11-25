The examples in this section reveal information about customers who use affinity cards or are likely to use affinity cards.

Example 1-2 Find Demographic Information About Preferred Customers

This query returns the gender, age, and length of residence of typical affinity card holders. The anomaly detection model, `SVMO_SH_Clas_sample`, returns `1` for typical cases and `0` for anomalies. The demographics are predicted for typical customers only; outliers are not included in the sample.

    SELECT cust_gender, round(avg(age)) age,
           round(avg(yrs_residence)) yrs_residence,
           count(*) cnt
    FROM mining_data_one_class_v
    WHERE PREDICTION(SVMO_SH_Clas_sample using *) = 1
    GROUP BY cust_gender
    ORDER BY cust_gender;

    CUST_GENDER         AGE YRS_RESIDENCE        CNT
    ------------ ---------- ------------- ----------
    F                    40             4         36
    M                    45             5        304

Example 1-3 Dynamically Identify Customers Who Resemble Preferred Customers

This query identifies customers who do not currently have an affinity card, but who share many of the characteristics of affinity card holders. The `PREDICTION` and `PREDICTION_PROBABILITY` functions use an `OVER` clause instead of a predefined model to classify the customers. The predictions and probabilities are computed dynamically.

    SELECT cust_id, pred_prob
     FROM
      (SELECT cust_id, affinity_card,
        PREDICTION(FOR TO_CHAR(affinity_card) USING *) OVER () pred_card,
        PREDICTION_PROBABILITY(FOR TO_CHAR(affinity_card),1 USING *) OVER () pred_prob
       FROM mining_data_build_v)
     WHERE affinity_card = 0
      AND pred_card = 1
     ORDER BY pred_prob DESC;

      CUST_ID PRED_PROB
    ---------- ---------
        102434       .96
        102365       .96
        102330       .96
        101733       .95
        102615       .94
        102686       .94
        102749       .93
    .
    .
    .
    .
        102580       .52
        102269       .52
        102533       .51
        101604       .51
        101656       .51

    226 rows selected.

Example 1-4 Predict the Likelihood that a New Customer Becomes a Preferred Customer

This query computes the probability of a first-time customer becoming a preferred customer (an affinity card holder). This query can be executed in real time at the point of sale.

The new customer is a 44-year-old American executive who has a bachelors degree and earns more than \$300,000/year. He is married, lives in a household of 3, and has lived in the same residence for the past 6 years. The probability of this customer becoming a typical affinity card holder is only 5.8%.

    SELECT PREDICTION_PROBABILITY(SVMO_SH_Clas_sample, 1 USING
                                 44 AS age,
                                 6 AS yrs_residence,
                                 'Bach.' AS education,
                                 'Married' AS cust_marital_status,
                                 'Exec.' AS occupation,
                                 'United States of America' AS country_name,
                                 'M' AS cust_gender,
                                 'L: 300,000 and above' AS cust_income_level,
                                 '3' AS houshold_size
                                 ) prob_typical
    FROM DUAL;

    PROB_TYPICAL
    ------------
      5.8

Example 1-5 Use Predictive Analytics to Find Top Predictors

The `DBMS_PREDICTIVE_ANALYTICS` PL/SQL package contains routines that perform simple data mining operations without a predefined model. In this example, the `EXPLAIN` routine computes the top predictors for affinity card ownership. The results show that household size, marital status, and age are the top three predictors.

    BEGIN
        DBMS_PREDICTIVE_ANALYTICS.EXPLAIN(
            data_table_name      => 'mining_data_test_v',
            explain_column_name  => 'affinity_card',
            result_table_name    => 'cust_explain_result');
    END;
    /

    SELECT * FROM cust_explain_result
      WHERE rank < 4;

    ATTRIBUTE_NAME           ATTRIBUTE_SUBNAME    EXPLANATORY_VALUE       RANK
    ------------------------ -------------------- ----------------- ----------
    HOUSEHOLD_SIZE                                       .209628541          1
    CUST_MARITAL_STATUS                                  .199794636          2
    AGE                                                  .111683067          3
