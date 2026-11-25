This interface method creates an Oracle Object or Collection by setting the attribute or element values respectively on the specified Oracle UDT.

### Declaration

    // C#
    void FromCustomObject(OracleConnection con, IntPtr pUdt);

### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  An opaque pointer to the Oracle Object or Collection to be created.

### Remarks

The `FromCustomObject` method is used to build an Oracle Object or Collection from a custom object by setting attribute or element values respectively through the `OracleUdt.SetValue` method.

The `OracleUdt.SetValue` method is invoked as follows:

- Oracle Object Type

  For a custom type that represents an Oracle Object Type, the `OracleUdt.SetValue` method must be invoked for each non-`NULL` attribute value that needs to be set.

- Oracle Collection Type

  For a custom type that represents an Oracle Collection Type, a single call to `OracleUdt.SetValue` method specifies the collection element values.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [IOracleCustomType Interface](IOracleCustomTypeInterface.md)

- [IOracleCustomType Members](IOracleCustomTypeMembers.md)
