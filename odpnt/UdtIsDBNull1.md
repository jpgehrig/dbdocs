This method indicates whether or not the attribute being retrieved, specified by `OracleConnection`, pointer, and attribute name, is `NULL`.

### Declaration

    // C#
    public static bool IsDBNull(OracleConnection con, IntPtr pUdt, string attrName);


### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  A pointer to an Oracle UDT.

- `attrName`

  The case-sensitive name of the attribute.

### Return Value

`True` if the specified attribute is `NULL`; otherwise, `false`.

### Exceptions

`ArgumentException` - The specified name is not a valid attribute name.

### Remarks

This method is invoked from the `IOracleCustomType.ToCustomObject` method. The `con` and `pUdt` parameter is passed from the `IOracleCustomType.ToCustomObject` method to the `OracleUdt.IsDBNull` method. The `attrName` parameter is case-sensitive.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleUdt Class](OracleUdtClass.md)

- [OracleUdt Members](OracleUdtMembers.md)
