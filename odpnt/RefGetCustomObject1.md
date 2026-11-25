This method returns the object that the specified `REF` references, as a custom type, using the specified fetch option.

### Declaration

    // C#
    public object GetCustomObject(OracleUdtFetchOption fetchOption);

### Parameters

- `fetchOption`

  An `OracleUdtFetchOption` value.

### Return Value

A custom object that represents the object that the specified `REF` references.

### Exceptions

`InvalidOperationException` - The specified connection is not open, or a valid custom type has not been registered for the type of the referenced object.

### Remarks

This method returns a custom type determined by the UDT mappings on the specified connection.

The connection must be opened explicitly by the application. This method does not open the connection implicitly.

The application can use the `OracleUdtFetchOption` method to control the copy of the Object that is returned according to the specified option:

- `OracleUdtFetchOption.Cache` option

  If this option is specified, and there is a copy of the referenced object in the object cache, it is returned immediately. If no cached copy exists, the latest copy of the referenced object in the database is cached in the object cache and returned.

- `OracleUdtFetchOption.Server` option

  If this option is specified, the latest copy of the referenced object from the database is cached in the object cache and returned. If a copy of the referenced object already exists in the cache, the latest copy overwrites the existing one.

- `OracleUdtFetchOption.TransactionCache` option

  If this option is specified, and a copy of the referenced object is cached in the current transaction, the copy is returned. Otherwise, the latest copy of the referenced object from the database is cached in the object cache and returned. If a copy of the referenced object already exists in the cache, the latest copy overwrites the existing one.

  Note that if a cached copy of the referenced object was modified before the current transaction began, that is, if the `OracleRef.HasChanges` property returns `true`, then the `Recent` option returns the cached copy of the referenced object. Outside of a transaction, the `Recent` option behaves like the `Any` option.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)

- "[OracleUdtFetchOption Enumeration](OracleUdtFetchOptionEnumeration.md)"
