This method returns a newly allocated `OracleUdtStatus` array of the specified length that will be used to store the null status of the collection elements.

### Declaration

    // C#
    Array CreateStatusArray(int numElems);

### Parameters

- `numElems`

  The number of collection elements to be returned.

### Return Value

A multi-dimensional `OracleUdtStatus` array as a `System.Array`.

### Remarks

An Oracle Collection Type can be represented in the following ways:

- As an array of the appropriate type. The type must be able to represent a collection element.

- As a Custom Type that contains an array of the appropriate type.

In both cases, the `CreateStatusArray` method creates an `OracleUdtStatus` array of the specified length that stores the null status of the collection elements.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [IOracleArrayTypeFactory Interface](IOracleArrayTypeFactoryInterface.md)

- [IOracleArrayTypeFactory Members](IOracleArrayTypeFactoryMembers.md)

- "[OracleUdtFetchOption Enumeration](OracleUdtFetchOptionEnumeration.md)"
