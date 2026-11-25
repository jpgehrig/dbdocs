Understand how you can transform data by using Automatic Data Preparation (ADP) and embedded data transformation.

A transformation is a SQL expression that modifies the data in one or more columns. Data must typically undergo certain transformations before it can be used to build a model. Many data mining algorithms have specific transformation requirements. Before data can be scored, it must be transformed in the same way that the training data was transformed.

Oracle Data Mining supports Automatic Data Preparation (ADP), which automatically implements the transformations required by the algorithm. The transformations are embedded in the model and automatically executed whenever the model is applied.

If additional transformations are required, you can specify them as SQL expressions and supply them as input when you create the model. These transformations are embedded in the model just as they are with ADP.

With automatic and embedded data transformation, most of the work of data preparation is handled for you. You can create a model and score multiple data sets in just a few steps:

1.  Identify the columns to include in the case table.

2.  Create nested columns if you want to include transactional data.

3.  Write SQL expressions for any transformations not handled by ADP.

4.  Create the model, supplying the SQL expressions (if specified) and identifying any columns that contain text data.

5.  Ensure that some or all of the columns in the scoring data have the same name and type as the columns used to train the model.

**Related Topics**

- [Scoring Requirements](data-requirements.md)
