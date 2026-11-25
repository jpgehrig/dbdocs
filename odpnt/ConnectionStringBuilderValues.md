This property specifies a collection of values contained in the Connection String Builder.

### Declaration

    // C#
    public override ICollection Values{get;}

### Property Value

Returns an `ICollection` that represents the values in the Connection String Builder.

### Remarks

The order of the values in the `ICollection` is unspecified, but is the same as the associated attributes in the `ICollection` returned by the `Keys` property.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
