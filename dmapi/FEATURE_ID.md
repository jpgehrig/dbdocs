### Syntax

### feature_id::=

![Description of feature_id.eps follows](img/feature_id.gif)
[Description of the illustration feature_id.eps](img_text/feature_id.md)

### Analytic Syntax

### feature_id_analytic::=

![Description of feature_id_analytic.eps follows](img/feature_id_analytic.gif)
[Description of the illustration feature_id_analytic.eps](img_text/feature_id_analytic.md)

### mining_attribute_clause::=

![Description of mining_attribute_clause.eps follows](img/mining_attribute_clause.gif)
[Description of the illustration mining_attribute_clause.eps](img_text/mining_attribute_clause.md)

### mining_analytic_clause::=

![Description of mining_analytic_clause.eps follows](img/mining_analytic_clause.gif)
[Description of the illustration mining_analytic_clause.eps](img_text/mining_analytic_clause.md)

**See Also:**

"[Analytic Functions](../sqlrf/Analytic-Functions.md)" for information on the syntax, semantics, and restrictions of `mining_analytic_clause`

### Purpose

`FEATURE_ID` returns the identifier of the highest value feature for each row in the selection. The feature identifier is returned as an Oracle `NUMBER`.

### Syntax Choice

`FEATURE_ID` can score the data in one of two ways: It can apply a mining model object to the data, or it can dynamically mine the data by executing an analytic clause that builds and applies one or more transient mining models. Choose Syntax or Analytic Syntax:

- Syntax — Use the first syntax to score the data with a pre-defined model. Supply the name of a feature extraction model.

- Analytic Syntax — Use the analytic syntax to score the data without a pre-defined model. Include `INTO` `n`, where `n` is the number of features to extract, and `mining_analytic_clause`, which specifies if the data should be partitioned for multiple model builds. The `mining_analytic_clause` supports a `query_partition_clause` and an `order_by_clause`. (See "[analytic_clause::=](../sqlrf/Analytic-Functions.md)".)

The syntax of the `FEATURE_ID` function can use an optional `GROUPING` hint when scoring a partitioned model. See [GROUPING Hint](../sqlrf/Comments.md).

### mining_attribute_clause

`mining_attribute_clause` identifies the column attributes to use as predictors for scoring. When the function is invoked with the analytic syntax, these predictors are also used for building the transient models. The `mining_attribute_clause` behaves as described for the `PREDICTION` function. (See "[mining_attribute_clause](../sqlrf/PREDICTION.md)".)

**See Also:**

- [Oracle Data Mining User's Guide](scoring-deployment.md) for information about scoring.

- [Oracle Data Mining Concepts](feature-selection-extraction.md) for information about feature extraction.

**Note:**

The following example is excerpted from the Data Mining sample programs. For more information about the sample programs, see Appendix A in [Oracle Data Mining User's Guide](../dmprg/data-mining-sample-programs.md).

### Example

This example lists the features and corresponding count of customers in a data set.

    SELECT FEATURE_ID(nmf_sh_sample USING *) AS feat, COUNT(*) AS cnt
      FROM nmf_sh_sample_apply_prepared
      GROUP BY FEATURE_ID(nmf_sh_sample USING *)
      ORDER BY cnt DESC, feat DESC;

          FEAT        CNT
    ---------- ----------
             7       1443
             2         49
             3          6
             6          1
             1          1
