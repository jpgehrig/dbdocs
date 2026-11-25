The data used by the sample data mining programs is based on these tables in the `SH` schema:

    SH.CUSTOMERS
    SH.SALES
    SH.PRODUCTS
    SH.SUPPLEMENTARY_DEMOGRAPHICS
    SH.COUNTRIES

The `dmshgrants` script grants `SELECT` access to the tables in `SH`. The `dmsh.sql` script creates views of the `SH` tables in the schema of the data mining user. The views are described in the following table:

Table A-2 The Data Mining Sample Data

| View Name                 | Description                                |
|:--------------------------|:-------------------------------------------|
| `MINING_DATA`             | Joins and filters data                     |
| `MINING_DATA_BUILD_V`     | Data for building models                   |
| `MINING_DATA_TEST_V`      | Data for testing models                    |
| `MINING_DATA_APPLY_V`     | Data to be scored                          |
| `MINING_BUILD_TEXT`       | Data for building models that include text |
| `MINING_TEST_TEXT`        | Data for testing models that include text  |
| `MINING_APPLY_TEXT`       | Data, including text columns, to be scored |
| `MINING_DATA_ONE_CLASS_V` | Data for anomaly detection                 |

The association rules program creates its own transactional data.
