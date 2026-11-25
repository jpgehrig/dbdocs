This interface initializes a custom object using the specified Oracle UDT.

### Declaration

    // C#
    void ToCustomObject (OracleConnection con, IntPtr pUdt);

### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  An opaque pointer to the Oracle UDT.

### Remarks

The `ToCustomObject` method is used to initialize a custom object from the specified Oracle Object or Collection by retrieving attribute or element values respectively through the `OracleUdt.GetValue` method.

The `OracleUdt.GetValue` method is invoked as follows:

- Oracle Object Type

  For a custom type that represents an Oracle Object Type, the `OracleUdt.GetValue` method must be invoked for each attribute value to be retrieved.

- For a custom type that represents an Oracle Collection Type, a single call to `OracleUdt.GetValue` method retrieves the collection element values.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [IOracleCustomType Interface](IOracleCustomTypeInterface.md)

- [IOracleCustomType Members](IOracleCustomTypeMembers.md)
