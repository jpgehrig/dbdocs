This property specifies if the transaction completed and that the information returned may be incomplete and/or not all expected work was completed.

### Declaration

    // C#
    public bool? UserCallCompleted {get;}

### Property Value

`bool`

### Remarks

If `GetOutcome()` is not called, the this property holds a `null` value.

Once `GetOutcome()` is called, then this property will hold either `true` or `false`.

In some cases, [GetOutcome](LogicalTransactionGetOutcomeOverloads.md) will be called implicitly and populate this property with a non-null value automatically

[Table 6-116](LogicalTransactionPublicPropertiesCommitted.md) describes the possible outcomes of the `Committed` and `UserCallCompleted` properties.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
