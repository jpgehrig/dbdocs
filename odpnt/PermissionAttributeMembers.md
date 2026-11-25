`OraclePermissionAttribute` members are listed in the following tables.

### OraclePermissionAttribute Constructor

The `OraclePermissionAttribute` constructor is listed in Table 6-142.

Table 6-142 OraclePermission Constructor

| Constructor                                                          | Description                                                           |
|:---------------------------------------------------------------------|:----------------------------------------------------------------------|
| [OraclePermissionAttribute Constructor](PermissionAttributeCtors.md) | Instantiates a new instance of the `OraclePermissionAttribute` class. |

### OraclePermissionAttribute Static Methods

The `OraclePermissionAttribute` static methods are listed in Table 6-143.

Table 6-143 OraclePermissionAttribute Static Methods

| Static Methods        | Description                                    |
|:----------------------|:-----------------------------------------------|
| `GetCustomAttribute`  | Inherited from `System.Attribute` (Overloaded) |
| `GetCustomAttributes` | Inherited from `System.Attribute`(Overloaded)  |
| `IsDefined`           | Inherited from `System.Attribute`(Overloaded)  |
| `ReferenceEquals`     | Inherited from `System.Object`                 |

### OraclePermissionAttribute Public Properties

The `OraclePermissionAttribute` public properties are listed in Table 6-144.

Table 6-144 OraclePermissionAttribute Public Properties

| Public Properties        | Description                                                                                                                                                                               |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Action `                | Inherited from `SecurityAttribute`                                                                                                                                                        |
| `AllowBlankPassword`     | Inherited from `DBDataPermissionAttribute`.<br>`OraclePermissionAttribute` ignores this property. Any value set for this property, for an `OraclePermissionAttribute` object, is ignored. |
| `ConnectionString`       | Inherited from `DBDataPermissionAttribute`                                                                                                                                                |
| `KeyRestrictionBehavior` | Inherited from `DBDataPermissionAttribute`                                                                                                                                                |
| `KeyRestrictions`        | Inherited from `DBDataPermissionAttribute`                                                                                                                                                |
| `TypeId`                 | Inherited from `System.Attribute`                                                                                                                                                         |
| `Unrestricted`           | Inherited from `SecurityAttribute`                                                                                                                                                        |

### OraclePermissionAttribute Public Methods

The `OraclePermissionAttribute` public methods are listed in Table 6-145.

Table 6-145 OraclePermissionAttribute Public Methods

| Public Methods                                             | Description                                                                                     |
|:-----------------------------------------------------------|:------------------------------------------------------------------------------------------------|
| [CreatePermission](PermissionAttributeCreatePermission.md) | Returns a new `OraclePermissionAttribute` object that is configured based on the attributes set |
| `Equals`                                                   | Inherited from `System.Attribute`                                                               |
| `GetHashCode`                                              | Inherited from `System.Attribute`                                                               |
| `GetType`                                                  | Inherited from `System.Attribute`                                                               |
| `IsDefaultAttribute`                                       | Inherited from `System.Attribute`                                                               |
| `Match`                                                    | Inherited from `System.Attribute`                                                               |
| `ShouldSerializeConnectionString`                          | Inherited from `DBDataPermissionAttribute`                                                      |
| `ShouldSerializeKeyRestrictions`                           | Inherited from `DBDataPermissionAttribute`                                                      |
| `ToString`                                                 | Inherited from `System.Object`                                                                  |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OraclePermissionAttribute Class](OraclePermissionAttributeClass.md)
