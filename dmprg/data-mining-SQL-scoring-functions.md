Understand the different data mining SQL scoring functions.

The Data Mining SQL language functions use Oracle Data Mining to score data. The functions can apply a mining model schema object to the data, or they can dynamically mine the data by executing an analytic clause. SQL functions are available for all the data mining algorithms that support the scoring operation. All Data Mining SQL functions, as listed in the following table can operate on R Mining Model with the corresponding mining function. However, the functions are not limited to the ones listed here.

Table 2-4 Data Mining SQL Functions

| Function                 | Description                                                                                                                                                |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CLUSTER_ID`             | Returns the ID of the predicted cluster                                                                                                                    |
| `CLUSTER_DETAILS`        | Returns detailed information about the predicted cluster                                                                                                   |
| `CLUSTER_DISTANCE`       | Returns the distance from the centroid of the predicted cluster                                                                                            |
| `CLUSTER_PROBABILITY`    | Returns the probability of a case belonging to a given cluster                                                                                             |
| `CLUSTER_SET`            | Returns a list of all possible clusters to which a given case belongs along with the associated probability of inclusion                                   |
| `FEATURE_COMPARE`        | Compares two similar and dissimilar set of texts from two different documents or keyword phrases or a combination of both                                  |
| `FEATURE_ID`             | Returns the ID of the feature with the highest coefficient value                                                                                           |
| `FEATURE_DETAILS`        | Returns detailed information about the predicted feature                                                                                                   |
| `FEATURE_SET`            | Returns a list of objects containing all possible features along with the associated coefficients                                                          |
| `FEATURE_VALUE`          | Returns the value of the predicted feature                                                                                                                 |
| `ORA_DM_PARTITION_NAME`  | Returns the partition names for a partitioned model                                                                                                        |
| `PREDICTION`             | Returns the best prediction for the target                                                                                                                 |
| `PREDICTION_BOUNDS`      | (GLM only) Returns the upper and lower bounds of the interval wherein the predicted values (linear regression) or probabilities (logistic regression) lie. |
| `PREDICTION_COST`        | Returns a measure of the cost of incorrect predictions                                                                                                     |
| `PREDICTION_DETAILS`     | Returns detailed information about the prediction                                                                                                          |
| `PREDICTION_PROBABILITY` | Returns the probability of the prediction                                                                                                                  |
| `PREDICTION_SET`         | Returns the results of a classification model, including the predictions and associated probabilities for each case                                        |

The following example shows a query that returns the results of the `CLUSTER_ID` function. The query applies the model `em_sh_clus_sample`, which finds groups of customers that share certain characteristics. The query returns the identifiers of the clusters and the number of customers in each cluster.

Example 2-9 CLUSTER_ID Function

    -- -List the clusters into which the customers in this
    -- -data set have been grouped.
    --
    SELECT CLUSTER_ID(em_sh_clus_sample USING *) AS clus, COUNT(*) AS cnt
      FROM mining_data_apply_v
    GROUP BY CLUSTER_ID(em_sh_clus_sample USING *)
    ORDER BY cnt DESC;

    SQL> -- List the clusters into which the customers in this
    SQL> -- data set have been grouped.
    SQL> --
    SQL> SELECT CLUSTER_ID(em_sh_clus_sample USING *) AS clus, COUNT(*) AS cnt
      2    FROM mining_data_apply_v
      3  GROUP BY CLUSTER_ID(em_sh_clus_sample USING *)
      4  ORDER BY cnt DESC;

          CLUS        CNT
    ---------- ----------
             9        311
             3        294
             7        215
            12        201
            17        123
            16        114
            14         86
            19         64
            15         56
            18         36

**Related Topics**

- [Scoring and Deployment](scoring-deployment.md)
- [Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md)
