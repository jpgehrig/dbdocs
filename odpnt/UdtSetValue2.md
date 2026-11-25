This method sets the attribute or elements on the specified Oracle UDT, using the specified index and value.

### Declaration

    // C#
    public static void SetValue(OracleConnection con, IntPtr pUdt, int attrIndex, object value);

### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  An opaque pointer to an Oracle UDT.

- `attrIndex`

  The index of the attribute to be set. Specify 0 for setting collection elements from a Custom Type that represents an Oracle Collection.

- `value`

  The attribute or collection value to be set.

### Exceptions

`ArgumentException` - The specified value is not of the appropriate type.

### Remarks

The `IOracleCustomType.FromCustomObject` method invokes `OracleUdt.SetValue` method passing it the `con` and `pUdt` parameters. The `OracleUdt.SetValue` method returns these types of object:

- Oracle Object Type

  For a Custom Type that represents an Oracle Object Type, the type accepted for a specified attribute index is the type of the member in the custom class or struct that is mapped to the attribute using the `OracleObjectMappingAttribute` object.

- Oracle Collection Type

  For a Custom Type that represents an Oracle Collection Type, the type accepted is the type of the member in the custom class or struct to which the `OracleArrayMappingAttribute` object is applied.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleUdt Class](OracleUdtClass.md)

- "[OracleUdt Members](OracleUdtMembers.md)"
