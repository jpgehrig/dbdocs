`OracleLoigcalTransaction` public read-only properties are listed in Table 6-115

Table 6-115 OracleLogicalTransaction Public Read-Only Properties

| Property                                                                          | Description                                                                                                                                |
|:----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| [Committed](LogicalTransactionPublicPropertiesCommitted.md)                       | Specifies if the transaction was committed or not                                                                                          |
| [ConnectionString](LogicalTransactionPublicPropertiesConnectionString.md)         | Specifies a subset of the connection string used for the transaction running during the last database outage                               |
| [LogicalTransactionId](LogicalTransactionPublicPropertiesLogicalTransactionId.md) | The logical transaction id is used to determine the commit outcome of the last transaction open in a database session following an outage. |
| [UserCallCompleted](LogicalTransactionPublicPropertiesUserCallCompleted.md)       | Specifies if the transaction completed and that the information returned may be incomplete and/or not all expected work was completed      |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
