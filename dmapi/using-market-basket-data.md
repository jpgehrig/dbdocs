Market basket data identifies the items sold in a set of baskets or transactions. Oracle Data Mining provides the association mining function for market basket analysis.

Association models use the Apriori algorithm to generate association rules that describe how items tend to be purchased in groups. For example, an association rule can assert that people who buy peanut butter are 80% likely to also buy jelly.

Market basket data is usually **transactional**. In transactional data, a case is a transaction and the data for a transaction is stored in multiple rows. Oracle Data Mining association models can be built on transactional data or on single-record case data. The `ODMS_ITEM_ID_COLUMN_NAME` and `ODMS_ITEM_VALUE_COLUMN_NAME` settings specify whether the data for association rules is in transactional format.

**Note:**

Association models are the only type of model that can be built on native transactional data. For all other types of models, Oracle Data Mining requires that the data be presented in single-record case format.

The Apriori algorithm assumes that the data is transactional and that it has many missing values. Apriori interprets all missing values as sparse data, and it has its own native mechanisms for handling sparse data.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](DBMS_DATA_MINING.md) for information on the `ODMS_ITEM_ID_COLUMN_NAME` and `ODMS_ITEM_VALUE_COLUMN_NAME` settings.

### 29.4.1 Example: Creating a Nested Column for Market Basket Analysis

The example shows how to define a nested column for market basket analysis.

Association models can be built on native transactional data or on nested data. The following example shows how to define a nested column for market basket analysis.

The following SQL statement transforms this data to a column of type `DM_NESTED_NUMERICALS` in a view called `SALES_TRANS_CUST_NESTED`. This view can be used as a case table for mining.

    CREATE VIEW sales_trans_cust_nested AS
                 SELECT trans_id,
                         CAST(COLLECT(DM_NESTED_NUMERICAL(
                         prod_name, 1))
                         AS DM_NESTED_NUMERICALS) custprods
                      FROM sales_trans_cust
                 GROUP BY trans_id;

This query returns two rows from the transformed data.

    SELECT * FROM sales_trans_cust_nested
                   WHERE trans_id < 101000
                   AND trans_id > 100997;

    TRANS_ID  CUSTPRODS(ATTRIBUTE_NAME, VALUE)
    -------  ------------------------------------------------
    100998   DM_NESTED_NUMERICALS
              (DM_NESTED_NUMERICAL('O/S Documentation Set - English', 1)
    100999   DM_NESTED_NUMERICALS
              (DM_NESTED_NUMERICAL('CD-RW, High Speed Pack of 5', 1),
               DM_NESTED_NUMERICAL('External 8X CD-ROM', 1),
               DM_NESTED_NUMERICAL('SIMM- 16MB PCMCIAII card', 1))

Example 29-7 Convert to a Nested Column

The view `SALES_TRANS_CUST` provides a list of transaction IDs to identify each market basket and a list of the products in each basket.

    describe sales_trans_cust
     Name                                                  Null?    Type
     ----------------------------------------------------- -------- ----------------
     TRANS_ID                                              NOT NULL NUMBER
     PROD_NAME                                             NOT NULL VARCHAR2(50)
     QUANTITY                                                       NUMBER

**Related Topics**

- [Handling Missing Values](handling-missing-values.md)
