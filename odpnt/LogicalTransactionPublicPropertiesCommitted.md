This property specifies if the transaction was committed or not.

### Declaration

    // C#
    public bool? Committed {get;}

### Property Value

`bool`.

### Remarks

If `GetOutcome()` is not called, the this property holds a `null` value.

Once `GetOutcome()` is called, then this property will hold either `true` or `false`.

In some cases, OracleLogicalTransaction.[GetOutcome](LogicalTransactionGetOutcomeOverloads.md) will be called implicitly and populate this property with a non-null value automatically.

Table 6-116 describes the possible outcomes of the `Committed` and `UserCallCompleted` properties.

Table 6-116 Outcome of OracleLogicalTransaction Committed and UserCallCompleted Properties

| Committed Value | UserCallCompleted Value | Outcome                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `false`         | `false`                 | The call did not execute the commit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `true`          | `true`                  | The call did execute the commit and there was no additional information to return and no more work to do if that call was a PL/SQL procedure.                                                                                                                                                                                                                                                                                                                                                                                      |
| `true`          | `false`                 | The transaction is committed, but the information returned may be incomplete and/or not all expected work was completed. Examples of incomplete information or incomplete work done include: the number of rows modified when using autocommit or commit on success, parameter and function results when calling PL/SQL procedures, or PL/SQL procedures with more work to do after the commit. In order to function correctly, .NET applications that use data returned from the commit must check the `UserCallCompleted` value. |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)
