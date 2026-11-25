`OracleLogicalTransaction` members are listed in the following tables.

### OracleLogicalTransaction Public Read-Only Properties

`OracleLoigcalTransaction` public read-only properties are listed in Table 6-113

Table 6-113 OracleLogicalTransaction Public Read-Only Properties

| Property                                                                          | Description                                                                                                                                |
|:----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| [Committed](LogicalTransactionPublicPropertiesCommitted.md)                       | Specifies if the transaction was committed or not                                                                                          |
| [ConnectionString](LogicalTransactionPublicPropertiesConnectionString.md)         | Specifies a subset of the connection string used for the transaction running during the last database outage                               |
| [LogicalTransactionId](LogicalTransactionPublicPropertiesLogicalTransactionId.md) | The logical transaction id is used to determine the commit outcome of the last transaction open in a database session following an outage. |
| [UserCallCompleted](LogicalTransactionPublicPropertiesUserCallCompleted.md)       | Specifies if the transaction completed and that the information returned may be incomplete and/or not all expected work was completed      |

### OracleLogicalTransaction Methods

`OracleLoigcalTransaction` methods are listed in Table 6-114

Table 6-114 OracleLogicalTransaction Methods

| Property                                               | Description                                                                                                                                               |
|:-------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Dispose](LogicalTransactionDispose.md)                | This method releases any resources or memory allocated by the object                                                                                      |
| [GetOutcome](LogicalTransactionGetOutcomeOverloads.md) | This method retrieves the transaction outcome from the database server. The method will determine whether the transaction committed and completed or not. |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)
