This method indicates whether or not the attribute being retrieved, specified by `OracleConnection`, pointer, and attribute index, is `NULL`.

### Declaration

    // C#
    public static bool IsDBNull(OracleConnection con, IntPtr pUdt, int attrIndex);


### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  An opaque pointer to an Oracle UDT.

- `attrIndex`

  The zero-based index of the attribute.

### Return Value

`True` if the specified attribute is `NULL`; otherwise, `false`.

### Exceptions

`ArgumentOutOfRangeException` - The specified index is not a valid attribute index

### Remarks

This method is invoked from the `IOracleCustomType.ToCustomObject` method. The `con` and `pUdt` parameter is passed from the `IOracleCustomType.ToCustomObject` method to the `OracleUdt.IsDBNull` method.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleUdt Class](OracleUdtClass.md)

- [OracleUdt Members](OracleUdtMembers.md)
