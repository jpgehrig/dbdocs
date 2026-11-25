The `APPLY` procedure in `DBMS_DATA_MINING` is a batch apply operation that writes the results of scoring directly to a table.

The columns in the table are mining function-dependent.

Scoring with `APPLY` generates the same results as scoring with the SQL scoring functions. Classification produces a prediction and a probability for each case; clustering produces a cluster ID and a probability for each case, and so on. The difference lies in the way that scoring results are captured and the mechanisms that can be used for retrieving them.

`APPLY` creates an output table with the columns shown in the following table:

Table 32-2 APPLY Output Table

| Mining Function    | Output Columns                               |
|:-------------------|:---------------------------------------------|
| classification     | `CASE_ID`<br>`PREDICTION`<br>`PROBABILITY`   |
| regression         | `CASE_ID`<br>`PREDICTION`                    |
| anomaly detection  | `CASE_ID`<br>`PREDICTION`<br>`PROBABILITY`   |
| clustering         | `CASE_ID`<br>`CLUSTER_ID`<br>`PROBABILITY`   |
| feature extraction | `CASE_ID`<br>`FEATURE_ID`<br>`MATCH_QUALITY` |

Since `APPLY` output is stored separately from the scoring data, it must be joined to the scoring data to support queries that include the scored rows. Thus any model that is used with `APPLY` must have a case ID.

A case ID is not required for models that is applied with SQL scoring functions. Likewise, storage and joins are not required, since scoring results are generated and consumed in real time within a SQL query.

The following example illustrates Anomaly Detection with `APPLY`. The query of the `APPLY` output table returns the ten first customers in the table. Each has a a probability for being typical (1) and a probability for being anomalous (0).

Example 32-15 Anomaly Detection with DBMS_DATA_MINING.APPLY

    EXEC dbms_data_mining.apply
            ('SVMO_SH_Clas_sample','svmo_sh_sample_prepared',
             'cust_id', 'one_class_output');

    SELECT * from one_class_output where rownum < 11;

       CUST_ID PREDICTION PROBABILITY
    ---------- ---------- -----------
        101798          1  .567389309
        101798          0  .432610691
        102276          1  .564922469
        102276          0  .435077531
        102404          1   .51213544
        102404          0   .48786456
        101891          1  .563474346
        101891          0  .436525654
        102815          0  .500663683
        102815          1  .499336317

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DATA_MINING.md)
