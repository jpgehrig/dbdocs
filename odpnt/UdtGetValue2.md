This method gets the attribute or elements from the specified Oracle UDT, using the specified index.

### Declaration

    // C#
    public static object GetValue(OracleConnection con, IntPtr pUdt, int attrIndex,);

### Parameters

- `con`

  An `OracleConnection` instance.

- `pUdt`

  A pointer to an Oracle UDT.

- `attrIndex`

  The zero-based index of the attribute to be retrieved. For retrieving collection elements from a Custom Type that represents an Oracle Collection, zero must be specified.

### Return Value

An object representing the returned attribute or collection elements.

### Exceptions

`ArgumentOutOfRangeException` - The specified index is not a valid attribute index.

### Remarks

The `IOracleCustomType.ToCustomObject` method invokes `OracleUdt.GetValue` method passing it the `con` and `pUdt` parameters. The `OracleUdt.GetValue` method returns these types of object:

- Oracle Object Type

  For a Custom Type that represents an Oracle Object Type, the type returned for a specified attribute index is the type of the member in the custom class or struct that is mapped to the attribute using the `OracleObjectMappingAttribute` object.

- Oracle Collection Type

  For a Custom Type that represents an Oracle Collection Type, the type returned is the type of the member in the custom class or struct to which the `OracleArrayMappingAttribute` object is applied.

In the case of `NULL` attribute values, the appropriate null representation of the type is returned. For example, for attributes that are represented as Custom Types and Provider Specific Types, the static `Null` property of the type is returned. For attributes that are represented as Nullable types, for example, `System.String` and `System.Array` Types, null is returned, and for all other remaining built-in types such as `Int32` and `DateTime` `DBNull.Value` is returned.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleUdt Class](OracleUdtClass.md)

- [OracleUdt Members](OracleUdtMembers.md)

- "[OracleUdtFetchOption Enumeration](OracleUdtFetchOptionEnumeration.md)"
