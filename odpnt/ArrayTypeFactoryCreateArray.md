This interface method returns a new array of the specified length to store Oracle Collection elements.

### Declaration

    // C#
    Array CreateArray(int numElems);

### Parameters

- `numElems`

  The number of collection elements to be returned.

### Return Value

A `System.Array` object.

### Remarks

An Oracle Collection Type may be represented in either of the following ways:

- As an array of the appropriate type. The type must be able to represent a collection element.

- As a Custom Type that contains an array of the appropriate type.

In both cases, the `CreateArray` method creates an array of the specified length to store the collection elements.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [IOracleArrayTypeFactory Interface](IOracleArrayTypeFactoryInterface.md)

- [IOracleArrayTypeFactory Members](IOracleArrayTypeFactoryMembers.md)
