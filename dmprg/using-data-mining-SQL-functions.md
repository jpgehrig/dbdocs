Learn about the benefits of SQL functions in data mining.

The data mining SQL functions provide the following benefits:

- Models can be easily deployed within the context of existing SQL applications.

- Scoring operations take advantage of existing query execution functionality. This provides performance benefits.

- Scoring results are pipelined, enabling the rows to be processed without requiring materialization.

The data mining techniques produce a score for each row in the selection. The functions can apply a mining model schema object to compute the score, or they can score dynamically without a pre-defined model, as described in "Dynamic Scoring".

**Related Topics**

- [Dynamic Scoring](dynamic-scoring.md)
- [Scoring Requirements](data-requirements.md)
-
- [Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md)

### 6.2.1 Choosing the Predictors

The SQL functions used for scoring support a `USING` clause that specifies which attributes to use for scoring. You can specify some or all of the attributes in the selection and you can specify expressions. The following examples all use the `PREDICTION` function to find the customers who are likely to use an affinity card, but each example uses a different set of predictors.

The query in Example 6-1 uses all the predictors.

The query in Example 6-2 uses only gender, marital status, occupation, and income as predictors.

The query in Example 6-3 uses three attributes and an expression as predictors. The prediction is based on gender, marital status, occupation, and the assumption that all customers are in the highest income bracket.

Example 6-1 Using All Predictors

    SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
         FROM mining_data_apply_v
         WHERE PREDICTION(dt_sh_clas_sample USING *) = 1
       GROUP BY cust_gender
       ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         25         38
    M        213         43

Example 6-2 Using Some Predictors

     SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
         FROM mining_data_apply_v
         WHERE PREDICTION(dt_sh_clas_sample USING
                          cust_gender,cust_marital_status,
                          occupation, cust_income_level) = 1
       GROUP BY cust_gender
       ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         30         38
    M        186         43

Example 6-3 Using Some Predictors and an Expression

    SELECT cust_gender, COUNT(*) AS cnt, ROUND(AVG(age)) AS avg_age
         FROM mining_data_apply_v
         WHERE PREDICTION(dt_sh_clas_sample USING
                         cust_gender, cust_marital_status, occupation,
                        'L: 300,000 and above' AS cust_income_level) = 1
       GROUP BY cust_gender
       ORDER BY cust_gender;

    C        CNT    AVG_AGE
    - ---------- ----------
    F         30         38
    M        186         43

### 6.2.2 Single-Record Scoring

The functions used for data mining can produce a score for a single record, as shown in Example 6-4 and Example 6-5.

Example 6-4 returns a prediction for customer 102001 by applying the classification model `NB_SH_Clas_sample`. The resulting score is 0, meaning that this customer is unlikely to use an affinity card.

Example 6-5 returns a prediction for 'Affinity card is great' as the comments attribute by applying the text mining model `T_SVM_Clas_sample`. The resulting score is 1, meaning that this customer is likely to use an affinity card.

Example 6-4 Scoring a Single Customer or a Single Text Expression

    SELECT PREDICTION (NB_SH_Clas_Sample USING *)
        FROM sh.customers where cust_id = 102001;

    PREDICTION(NB_SH_CLAS_SAMPLEUSING*)
    -----------------------------------
                                      0

Example 6-5 Scoring a Single Text Expression

    SELECT
      PREDICTION(T_SVM_Clas_sample USING 'Affinity card is great' AS comments)
    FROM DUAL;

    PREDICTION(T_SVM_CLAS_SAMPLEUSING'AFFINITYCARDISGREAT'ASCOMMENTS)
    -----------------------------------------------------------------
                                                                    1
