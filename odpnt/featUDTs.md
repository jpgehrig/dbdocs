ODP.NET has the ability to represent Oracle UDTs found in the database as custom types in .NET applications. UDTs are useful in representing complex entities as a single object that can be shared among applications. Oracle products, such as Oracle Spatial and Oracle XML DB, use their own complex types frequently.

To represent Oracle UDTs as .NET custom types, applications must apply .NET attributes to custom classes and structs, and to their public fields and properties.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support UDTs and .NET Custom Types

To convert between UDTs and custom types, ODP.NET uses custom interfaces.

This section discusses the following topics:

- Oracle User-Defined Types (UDTs)

- Custom Types

- Specifying Custom Type Mappings

- Converting Between Custom Types and Oracle UDTs

- Oracle UDT Attribute Mappings

- Oracle UDT Retrieval from OracleDataReader

- Oracle UDT Metadata Retrieval from OracleDataReader

- Oracle UDT Parameter Binding with OracleParameter

- Populating the DataSet with Oracle UDTs

- UDT Method Invocation

- Configuration Settings for Oracle UDTs

### Oracle User-Defined Types (UDTs)

Oracle Data Provider for .NET supports Oracle object types or user-defined types (UDTs), which are defined in the Oracle database.

There are two kinds of UDTs:

- Object types (Oracle Object)

- Collection types (which can be `VARRAY` types or nested table types)

Additionally, ODP.NET supports references (`REF`) to object types.

The term UDT is used interchangeably with Oracle object types and abstract data types (ADTs).

The name of the Oracle UDT is case-sensitive and must be in the form `schema_name.type_name`.

UDT samples in installations done using ODAC Oracle Universal Installer are provided in the `ORACLE_BASE\\ORACLE_HOME``\ODP.NET\Samples\UDT` directory.

**See Also:**

- "[OracleRef Class](OracleRefClass.md)"

- [Oracle Database Object-Relational Developer's Guide](../adobj/about-oracle-objects.md) for complete descriptions of object types

### Custom Types

Oracle Data Provider for .NET supports UDTs by representing Oracle UDTs defined in the database as .NET types, that is, custom types. For every Oracle UDT that the application wishes to fetch and manipulate, one custom type factory and one custom type are needed. The custom factory class is solely responsible for instantiating the custom type. ODP.NET uses the interfaces implemented on the custom factory classes to instantiate custom types at run time. Custom types define the mapping between the Oracle UDT attributes or elements to the .NET members. ODP.NET uses the interfaces implemented on the custom type instances to transfer values between the Oracle UDT and the custom type at run time.

Custom types can be .NET classes or structures. They can represent either Oracle Objects or Oracle Collections. Custom types can be implemented manually by the application developer or generated through an ODP.NET code generation tool.

Once the factory class and the custom type are defined and meet the implementation requirements, the application may set ODP.NET to automatically discover the mapping between the Oracle UDT and the custom type. This discovery process is based on the attribute that is applied on the custom factory class. Alternatively, the application can provide an explicit mapping through a configuration file.

Oracle Collections can be represented as an array of .NET Types. For example, an Oracle Collection type of `NUMBER` can be mapped to an `int[]`. Moreover, an Oracle Collection type of an Oracle UDT can be mapped to an array of the custom type.

Custom types must adhere to certain requirements in order for ODP.NET to represent Oracle UDTs as custom types. These requirements are as follows:

#### Required Custom Type Implementations

This section lists the required implementations for a custom .NET class or structure.

- `Oracle.DataAcess.Types.IOracleCustomType` interface implementation

  This interface is used for conversions between custom types and Oracle UDTs.

  The interface methods are implemented using the static methods of the `OracleUdt` class.

- Custom Type Factories

  A custom type factory is used to create an instance of a custom type. A custom type factory is an implementation of either the `IOracleCustomTypeFactory` interface, the `IOracleArrayTypeFactory` interface, or both interfaces, as follows:

  - To create a custom type that represents an Oracle Object, the custom type or a separate custom type factory class must implement the `Oracle.DataAccess.Types.IOracleCustomTypeFactory` interface.

  - To create a custom type that represents an Oracle Collection, the custom type or a separate custom type factory class must implement the `Oracle.DataAccess.Types.IOracleCustomTypeFactory` interface and the `Oracle.DataAccess.Types.IOracleArrayTypeFactory` interface.

  - To create an array type that represents an Oracle Collection, a custom type factory class must implement the `Oracle.DataAccess.Types.IOracleArrayTypeFactory` interface.

- Custom Type Member Mapping Attributes

  The custom type member mapping attributes specify the mapping between custom type members and either Oracle object attributes or Oracle collection elements.

  There are two types of custom type member mapping attributes:

  - `OracleObjectMappingAttribute`

    This attribute specifies the mapping between custom type members and Oracle object attributes for custom types that represent Oracle objects. This attribute must be applied to each custom type member (either field or property) that represents an Oracle Object attribute.

    **Note:**

    Not all Oracle object attributes need to be mapped to custom type members. If there is no `OracleObjectMappingAttribute` for a particular object attribute, ODP.NET ignores that object attribute when converting between Oracle objects and custom types.

  - `OracleArrayMappingAttribute`

    This attribute specifies the custom type member that stores the elements of an Oracle collection for custom types representing Oracle collections.The attribute must be specified on only one of the custom type members.

- `Oracle.DataAcess.Types.INullable` interface implementation

  This interface is used to determine if an instance of a custom type represents a null UDT. The `IsNull` property of the interface enables applications and ODP.NET to determine whether or not the UDT is null.

- Static Null field

  The public static `Null` property is used to return a null UDT. This property returns a custom type with an `IsNull` property that returns true.

#### Optional Custom Type Implementations

The following are optional:

- `IXMLSerializable`

  The `IXMLSerializable` interface is used in the .NET 2.0 framework to enable conversion between the custom type and its XML representation.This interface is only used if the serialization and deserialization of a custom type is needed in the `DataSet`.

- `Static Parse` and `Public ToString` methods

  These methods enable conversion between the custom type and its string representation.

  These methods are invoked when a `DataGrid` control is used to accept changes and display instance values.

- Type Inheritance

  Type Inheritance refers to the process of deriving an Oracle UDT in the database from a super type.

  If the custom type represents an Oracle UDT that is derived from a super type, the custom class should follow the same type hierarchy, that is, the custom class should be derived from another custom class that represents the super type defined in the database.

- `OracleCustomTypeMappingAttribute`

  The `OracleCustomTypeMappingAttribute` object specifies the mapping between a custom type (or an array type) and an Oracle UDT.

  There must be a unique custom type factory for each Oracle UDT used by the application as follows:

  - Oracle Object Types:

    The custom type factory must return a custom type that only represents the specified Oracle Object Type.

  - Oracle Collection Types:

    The custom type factory may return a custom type that can be used by other Oracle Collection Types. This is common when an array type is used to represent an Oracle Collection, for example, when an `int[]` is used to represent a collection of `NUMBER`s.

  If the `OracleCustomTypeMappingAttribute` is not specified, then custom type mappings must be specified through XML configuration files, that is, `machine.config`, and either `app.config` for Windows applications or `web.config` for web applications.

**See Also:**

- "[IOracleCustomType Interface](IOracleCustomTypeInterface.md)"

- "[OracleRef Class](OracleRefClass.md)"

- "[IOracleCustomTypeFactory Interface](IOracleCustomTypeFactoryInterface.md)"

### Specifying Custom Type Mappings

After creating a custom type, the application must specify a custom type mapping that maps the custom type to an Oracle UDT in the database. This can be done using a custom type factory or XML in configuration files.

Using XML to specify custom type mappings has priority, if both techniques have been implemented. At run time, if ODP.NET finds custom type mappings specified in configuration files, it ignores any custom type mappings specified through the `OracleCustomTypeMappingAttribute` object. If a .NET application dynamically loads .NET assemblies, which contain .NET classes that Oracle UDTs are mapped to, then the mapping between .NET classes and Oracle UDTs must be configured using a .NET config file.

Custom type mappings cannot be specified using synonyms, regardless of whether or not the mapping is provided through the `OracleCustomTypeMappingAttribute` object or the XML configuration file.

**See Also:**

Oracle Developer Tools for Visual Studio help sections on User-Defined Types Node under Server Explorer in Visual Studio for further information on UDT mapping.

This section contains these topics:

- "Using a Custom Type Factory to Specify Custom Type Mappings"

- "Using XML in Configuration Files to Specify Custom Type Mappings"

#### Using a Custom Type Factory to Specify Custom Type Mappings

The application can specify a custom type mapping using a custom type factory. The application supplies the name of the Oracle UDT, in the format `schema_name.type_name`, to an `OracleCustomTypeMappingAttribute` object and applies the name to the corresponding custom type factory. A custom type factory is a class or struct that implements either or both the `IOracleCustomTypeFactory` and `IOracleArrayTypeFactory` interfaces.

Note that for each Oracle UDT used by the application, there must be a unique custom type factory. Additionally, for Oracle Object Types, the custom type factory must return a custom type that uniquely represents the specified Oracle Object Type. For Oracle Collection Types, the custom type factory returns a custom type that can be used by other Oracle Collection Types. This is common when an custom type that is an array type represents an Oracle Collection, that is, when an `int[]` is used to represent a collection of `NUMBER`s.

At run time, using reflection programming, ODP.NET discovers all the custom type mappings specified by the application through the `OracleCustomTypeMappingAttribute` object.

**Note:**

The UDT name that is specified in the `OracleCustomTypeMappingAttribute` may not contain a period.

#### Using XML in Configuration Files to Specify Custom Type Mappings

The application can specify a custom type mapping with XML in configuration files, for example: using `machine.config`, and either `app.config` for Windows applications or `web.config` for web applications.

The custom type mappings must be specified in the `oracle.dataaccess.client` configuration section group. Each custom type mapping must be added to the collection of custom type mappings using the XML element `<add>`.

Each custom type mapping is consists of a name attribute and a value attribute. The name attribute may be any user-specified name that represents the custom type mapping. The value attribute must begin with `udtMapping` and be followed by the required and optional attributes listed below.

##### Required Attributes

- `factoryName`

  The case-sensitive assembly qualified name of the custom type factory class or struct.

  If the assembly that defines the custom type factory does not have a strong name, then a partial assembly name consisting of just the assembly name is sufficient. In the case of strongly named assemblies, a complete assembly name is required. It must include the assembly name, the `Version`, `Culture`, `PublicKeyToken`.

- `typeName`

  The case-sensitive name of the UDT defined in the database. By default all UDTs are created in the database with upper case names

- `schemaName`

  The case-sensitive schema in which the UDT is defined in the database. By default all schemas are created in the database with upper case names

##### Optional Attributes

- `dataSource`

  If specified, indicates that the custom type mapping applies only to Oracle UDTs defined in the database that the application connects to, as specified by the TNS name alias.

  The Data Source is case-insensitive.

The following is an example of the format of the XML that can be specified in the configuration file for .NET 2.0:

     <oracle.dataaccess.client>
        <settings>
          <add name="Person" value="udtMapping factoryName='Sample.PersonFactory,
              Sample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null'
              typeName='PERSON' schemaName='SCOTT' dataSource='oracle'"/>
          <add name="Student" value="udtMapping factoryName='Sample.StudentFactory,
              Sample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null'
              typeName='STUDENT' schemaName='SCOTT'"/>
        </settings>
      </oracle.dataaccess.client>

#### Using Custom Type Mappings

During data retrieval, the application uses the custom type mappings to convert an Oracle UDT to a custom type. When data is provided back to the database through an input or input/output parameter, or by an update through an Oracle `REF`, the application uses the mappings to convert the custom type to an Oracle UDT.

In the case of input and input/output parameters, the application must also set the `OracleParameter` `UdtTypeName` property to the user-defined type name of the parameter.

In certain cases, where Oracle UDTs are part of a type hierarchy, the custom type must be instantiated as a specific type in the type hierarchy. The Oracle UDT provided by the custom type mapping must a subtype of the Oracle UDT specified by the `OracleParameter` `UdtTypeName` property.

For example, the parameter for a stored procedure is of type, `SCOTT.PERSON` and has a subtype, `SCOTT.STUDENT`. The application has a custom class instance that represents `SCOTT.STUDENT`. The `UdtTypeName` is set to `SCOTT.PERSON`, but the custom type mapping indicates that the custom class is mapped to `SCOTT.STUDENT` and overrides the `UdtTypeName` when it instantiates the Oracle UDT. Thus, ODP.NET instantiates and binds Oracle UDTs appropriately when the custom object represents an Oracle UDT that is a subtype of the parameter type.

### Converting Between Custom Types and Oracle UDTs

ODP.NET can convert between Oracle UDTs and custom types, if the proper attribute mappings are specified and the custom types are defined properly.

ODP.NET performs a conversion whenever an Oracle UDT is fetched as:

- In, out, in/out parameters bound for SQL or PL/SQL execution

  The `DbType` property of `OracleParameter` must be set to `DbType.Object` or the `OracleDbType` property must be set to `OracleDbType.Object` or `OracleDbType.Array`.

  For parameters that are user-defined types, the `UdtTypeName` property of the `OracleParameter` object must be always set to the parameter type.

  Note: The `UdtTypeName` may differ from the Oracle UDT specified in the custom type mapping. This is the case when the parameter type is a super type of the Oracle UDT that the custom type represents.

- Column value retrieved from an `OracleDataReader` object

  If the application requests for the value either through the `GetValue`, `GetValues`, `GetOracleValue`, `GetOracleValues`, `GetProviderSpecificValue`, or `GetProviderSpecificValues` methods or the `Item[]` property for a UDT column, ODP.NET finds the corresponding custom type that represents the Oracle UDT and carries out the proper conversion.

- Part of a Resultset that populates the `DataSet`

  If the application populates the `DataSet` with a result that contains UDTs using the `Fill` method on the `OracleDataAdapter`, the `DataSet` is populated with custom types that represent Oracle UDTs. With ADO.NET 2.0, the `DataSet` is populated with custom types for UDT columns regardless of whether the `ReturnProviderSpecificTypes` on the `OracleDataAdapter` is set to `true` or `false`.

- A Object referenced through a `REF`

  When an Object referenced by a `REF` is retrieved, the custom type that represents the Oracle UDT is returned.

  The application can use the `OracleUdtFetchOption` method to control the copy of the Object that is returned as follows:

  - If the `OracleUdtFetchOption.Cache` option is specified and a cached copy of the object exists, the cached copy is immediately returned. If no cached copy exists, the latest object copy from the database is cached and returned.

  - If the `OracleUdtFetchOption.Server` option is specified, the latest object copy from the database is cached and returned. If the object is already cached, the latest object copy overwrites the existing one.

  - If the `OracleUdtFetchOption.TransactionCache` option is specified, there are two possibilities within the same transaction:

    - If the object copy was previously retrieved using the `Server` or `TransactionCache` option, the `TransactionCache` option behavior becomes equivalent to the `Cache` option behavior.

    - If the object copy was not previously retrieved using the Server or `TransactionCache` option, the `TransactionCache` option behavior becomes equivalent to the `Server` option behavior.

### Oracle UDT Attribute Mappings

Table 3-21 lists valid mappings of attributes (for objects) and elements (for collections), between Oracle UDT types and custom object types which can be either .NET types or Oracle provider-specific types (ODP.NET types).

Oracle collections do not have to map to a custom class. They can map to arrays of a specific type. Table 3-21 indicates those collections with elements of a specified Oracle type that can map to arrays of a .NET Type or a provider-specific type. For example, if an Oracle Collection is a `VARRAY` of `NUMBER(8)`, it can map to a `typeof(int[]`). This eliminates the need to construct a class that only holds an `int[]`.

For .NET 2.0, Oracle Collections can be mapped to Nullable types. This allows .NET 2.0 applications to obtain a nullable `int[]` which can hold null values in the `int[]`.

Note that Oracle UDT attributes and elements cannot be mapped to `object` or `object[]`.

Table 3-21 Attribute Mappings Between UDTs and Custom Object Types

| Type of UDT Attribute or Element         | .NET Type                                                                                                | ODP.NET Type         |
|:-----------------------------------------|:---------------------------------------------------------------------------------------------------------|:---------------------|
| `BFILE` \#1                              | `System.Byte[]`                                                                                          | `OracleBFile`        |
| `BINARY` `FLOAT`                         | `System.Byte, System.Int16, System.Int32, System.Int64, System.Single, System.Double, ` `System.Decimal` | `OracleDecimal`      |
| `BINARY` `DOUBLE`                        | `System.Byte, System.Int16, System.Int32, System.Int64, System.Single, System.Double, ` `System.Decimal` | `OracleDecimal`      |
| `BLOB`                                   | `System.Byte[]`                                                                                          | `OracleBlob`         |
| `CHAR`                                   | `System.Char[]`, `System.String`                                                                         | `OracleString`       |
| `CLOB`                                   | `System.Char[]`, `System.String`                                                                         | `OracleClob`         |
| `DATE`                                   | `System.DateTime`                                                                                        | `OracleDate`         |
| `INTERVAL` `DAY` `TO` `SECOND`           | `System.TimeSpan`,                                                                                       | `OracleIntervalDS`   |
| `INTERVAL` `YEAR` `TO` `MONTH`           | `System.Int64`                                                                                           | `OracleIntervalYM`   |
| `LONG` `RAW`                             | `System.Byte[]`                                                                                          | `OracleBinary`       |
| `NCHAR`                                  | `System.Char[]`, `System.String`                                                                         | `OracleString`       |
| `NCLOB`                                  | `System.Char[]`, `System.String`                                                                         | `OracleClob`         |
| Nested Table                             | `custom type`, `.NET type[]`, or `custom type`\[\]                                                       | `ODP Type[]`         |
| `NUMBER`                                 | `System.Byte, System.Int16, System.Int32, System.Int64, System.Single, System.Double, ` `System.Decimal` | `OracleDecimal`      |
| `NVARCHAR2`                              | `System.Char[]`, `System.String`                                                                         | `OracleString`       |
| Object Type                              | `custom type`                                                                                            | N/A                  |
| `RAW`                                    | `System.Byte[]`                                                                                          | `OracleBinary`       |
| `REF`                                    | `System.String`                                                                                          | `OracleRef`          |
| `TIMESTAMP`                              | `System.DateTime`                                                                                        | `OracleTimeStamp`    |
| `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` | `System.DateTime`                                                                                        | `OracleTimeStampLTZ` |
| `TIMESTAMP` `WITH` `TIME` `ZONE`         | `System.DateTime`                                                                                        | `OracleTimeStampTZ`  |
| `VARCHAR2`                               | `System.Char[]`, `System.String`                                                                         | `OracleString`       |
| `VARRAY`                                 | `custom type`, `.NET type[]`, or `custom type`\[\]                                                       | `ODP Type[]`         |

Notes:

1.  Conversion from a `System.Byte[]` to a `BFILE` is not supported, and therefore, `System.Byte[]` only represents a `BFILE` in read-only scenarios.

### Oracle UDT Retrieval from OracleDataReader

In order to retrieve Oracle UDTs from the `OracleDataReader`, an application must specify a custom type mapping that determines the type that will represent the Oracle UDT. Once a custom type mapping has been specified and any necessary custom types have been created, the application can retrieve Oracle UDTs.

Table 3-22 shows the type and value returned from an `OracleDataReader` object based on the method invoked, the column type, and whether or not there is a valid Custom type mapping.

**Note:**

`PS Object` refers to a provider-specific object.

Table 3-22 Type and Value Returned from OracleDataReader Object

| OracleDataReader method/property invocation                                                                            | Column Data Type       | Custom Type Mapping   | Value Returned for Oracle UDT                                       | NULL Value Returned for Oracle UDT |
|:-----------------------------------------------------------------------------------------------------------------------|:-----------------------|:----------------------|:--------------------------------------------------------------------|:-----------------------------------|
| `Item[index]`, `Item[name]`, `GetValue()`, `GetValues()`                                                               | `Object`, `Collection` | none                  | Exception thrown                                                    | Exception thrown                   |
| `Item[index]`, `Item[name]`, `GetValue()`, `GetValues()`                                                               | `Object`               | `schema.type`         | `custom object`                                                     | `DBNull.Value`                     |
| `Item[index]`, `Item[name]`, `GetValue()`, `GetValues()`                                                               | `Collection`           | `schema.type`         | `custom object | custom object[]` \| `.NET Type[]` \| `PS object[]` | `DBNull.Value`                     |
| `Item[index]`, `Item[name]`, `GetValue()`, `GetValues()`                                                               | `REF`                  | none \| `schema.type` | `string` (HEX)                                                      | `DBNull.Value`                     |
| `GetString()`                                                                                                          | `REF`                  | none \| `schema.type` | `string` (HEX)                                                      | Exception thrown                   |
| `GetProviderSpecificValue()`, `GetProviderSpecificValues()`, `GetOracleValue()`, `GetOracleValues()`                   | `Object`, `Collection` | `schema.type`         | `custom object`                                                     | `custom type`.`Null`               |
| `GetProviderSpecificValue()`, `GetProviderSpecificValues()`, `GetOracleValue()`, `GetOracleValues()`                   | `Collection`           | `schema.type`         | `custom object[]` \| `.NET Type[]` \| `PS object[]`                 | `null`                             |
| `GetProviderSpecificValue()`, `GetProviderSpecificValues()`, `GetOracleValue()`, `GetOracleValues()`, `GetOracleRef()` | `REF`                  | none \| `schema.type` | `OracleRef`                                                         | `OracleRef.Null`                   |
| `GetOracleString()`                                                                                                    | `REF`                  | none \| `schema.type` | `OracleString` (HEX)                                                | `OracleString.Null`                |

**See Also:**

"[Obtaining Data from an OracleDataReader Object](featData.md)"

### Oracle UDT Metadata Retrieval from OracleDataReader

An `OracleDataReader` object can return metadata used to determine the custom type that represents an Oracle UDT when a .NET Type or Provider-Specific Type accessor is invoked. The same custom type is used when populating the `DataSet` using the `OracleDataAdapter.Fill` method.

Table 3-23 shows the values returned from the `OracleDataReader` `GetFieldType` and `GetProviderSpecificFieldType` methods that specify the .NET type of the column.

Table 3-23 Values Returned from OracleDataReader Methods

| OracleDataReader Method/Property invocation | Column Data Type       | Custom Type Mapping   | Return Value                                                                                                 |
|:--------------------------------------------|:-----------------------|:----------------------|:-------------------------------------------------------------------------------------------------------------|
| `GetFieldType(index)`                       | `Object`, `Collection` | none                  | Exception thrown                                                                                             |
| `GetFieldType(index)`                       | `Object`               | `schema.type`         | `typeof(``custom type``)`                                                                                    |
| `GetFieldType(index)`                       | `Collection`           | `schema.type`         | `typeof(``custom type``)` \| `typeof(``custom type[]))` \| `typeof(``.NET type[])`) \| `typeof(``PS type[])` |
| `GetFieldType(index)`                       | `REF`                  | none \| `schema.type` | `typeof(string)`                                                                                             |
| `GetProviderSpecificFieldType(index)`       | `Object`, `Collection` | none                  | Exception thrown                                                                                             |
| `GetProviderSpecificFieldType(index)`       | `Object`,              | `schema.type`         | `typeof(``custom type``)`                                                                                    |
| `GetProviderSpecificFieldType(index)`       | `Collection`           | `schema.type`         | `typeof(``custom type``)` \| `typeof(``custom type[]))` \| `typeof(``.NET type[])`) \| `typeof(``PS type[])` |
| `GetProviderSpecificFieldType(index)`       | `REF`                  | none \| `schema.type` | `typeof(OracleRef)`                                                                                          |

### Oracle UDT Parameter Binding with OracleParameter

This section discusses using UDT output and input parameter bindings with an `OracleParameter` object.

**See Also:**

"[Parameter Binding](featOraCommand.md)"

This section contains these topics:

- Guidelines for Binding UDT Input and Output Parameters

- UDT Input Parameter Binding with OracleParameters

- UDT Output Parameter Binding with OracleParameters

#### Guidelines for Binding UDT Input and Output Parameters

Developers must consider the following when using UDT parameter bindings with an `OracleParameter` object.

- The `UdtTypeName` property must be set. Binding is based on the `UdtTypeName` property regardless of the parameter direction.

  **Note:**

  The `UdtTypeName` may differ from the Oracle UDT specified in the custom type mapping. This occurs when the parameter type is a super type of the Oracle UDT that the custom type represents.

- In case of Input/Output binding, the behavior is the same as Input and Output parameters.

- For Input parameter values, the bind value is converted to the UDT specified by the custom type mapping.

- For Output parameters:

  - If the value being returned is an Oracle Object or Collection, it is converted to a custom type or array type as specified by the custom type mapping. The value returned is always a custom type or an array type, regardless of whether the property most recently set was `DbType` or `OracleDbType`.

  - If the value being returned is a `REF`, then no custom type mapping is required.

#### UDT Input Parameter Binding with OracleParameters

Only certain combinations of these `OracleParameter` property values, `DbType`, `OracleDbType`, and `UdtTypeName`, can exist on the `OracleParameter` object. `OracleParameter` objects cannot be set to combinations that are not listed.

Table 3-24 describes the valid ways of binding input parameters for Oracle UDTs.

The last column indicates the Oracle type that ODP.NET converts the `OracleParameter` value to before binding.

Table 3-24 Valid Ways to Bind Input Parameters for Oracle UDTs

| OracleParameter. Value                                                                                                         | OracleParameter. DbType or OracleParameter. OracleDbType                                  | OracleParameter. UdtTypeName | Custom Type Mappings  | Oracle Type converted to before Binding                                                                    |
|:-------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------|:-----------------------------|:----------------------|:-----------------------------------------------------------------------------------------------------------|
| `custom object` \| `custom object[]` \|`.NET object[] `\|`PS object[]` \| `String` (HEX) \| `OracleString`(HEX) \| `OracleRef` | `DbType.Object` \| `OracleDbType.Object` \| `OracleDbType.Array` \| `OracleDbType.Ref` \| | not set                      | none \| `schema.type` | Exception thrown                                                                                           |
| `custom object[]` \|`.NET object[] `\|`PS object[]`                                                                            | `DbType.Object` \| `OracleDbType.Object` \| `OracleDbType.Array`                          | `schema.type`                | none                  | Exception thrown                                                                                           |
| `custom object`                                                                                                                | `DbType.Object`                                                                           | `schema.type`                | `schema.type`         | Specified UDT is instantiated. Value is bound as Object or Collection, based on the `UdtTypeName` property |
| `custom object`                                                                                                                | `OracleDbType.Object`                                                                     | `schema.type`                | `schema.type`         | Specified UDT is instantiated. `schema.type` must represent an object.                                     |
| `custom object`                                                                                                                | `OracleDbType.Array`                                                                      | `schema.type`                | `schema.type`         | Specified UDT is instantiated. `schema.type` must represent a collection.                                  |
| `.NET object[] | PS object[] | custom object[]`                                                                                | `DbType.Object` \| `OracleDbType.Array`                                                   | `schema.type`                | `schema.type`         | UDT specified by `OracleParameter.UdtTypeName` is instantiated.                                            |
| `.NET object[] | PS object[] | custom object[]`                                                                                | `OracleDbType.Object`                                                                     | `schema.type`                | none \| `schema.type` | Exception thrown                                                                                           |
| `custom object `\|`.NET object[] `\|`PS object[]` `custom object[]`                                                            | `OracleDbType.Ref`                                                                        | `schema.type`                | none \| `schema.type` | Exception thrown                                                                                           |
| `String` (HEX) \| `OracleString` (HEX) \| `OracleRef`                                                                          | `DbType.Object` \| `OracleDbType.Object` \| `OracleDbType.Array`                          | `schema.type`                | none \| `schema.type` | Exception thrown                                                                                           |
| Char\[\] (HEX) \| `String` (HEX) \|`OracleString` (HEX) \| `OracleRef`                                                         | `OracleDbType.Ref`                                                                        | `schema.type`                | none \| `schema.type` | A `REF`                                                                                                    |

#### UDT Output Parameter Binding with OracleParameters

Only certain combinations of these `OracleParameter` property values, `DbType`, `OracleDbType`, and `UdtTypeName`, can exist on the `OracleParameter` object. `OracleParameter` objects cannot be set to combinations that are not listed.

Table 3-25 shows the supported ODP.NET output parameter bindings of Oracle database objects.

The last column indicates the type that ODP.NET converts the `OracleParameter` value to before binding.

Table 3-25 Valid Ways to Bind Output Parameters for Oracle UDTs

| Type returned from Oracle   | OracleParameter. DbType                                                                | OracleParameter. UdtTypeName | Custom Type Mappings  | Type converted to                                                        |
|:----------------------------|:---------------------------------------------------------------------------------------|:-----------------------------|:----------------------|:-------------------------------------------------------------------------|
| `Object`/`Collection`/`REF` | `DbType.Object` \| `OracleDbType.Object` \| `OracleDbType.Array` \| `OracleDbType.Ref` | not set                      | none \| `schema.type` | Exception thrown                                                         |
| `Object`/`Collection`       | `DbType.Object` \| `OracleDbType.Object` \| `OracleDbType.Array`                       | `schema.type`                | none                  | Exception thrown                                                         |
| `Object`                    | `DbType.Object` \| `OracleDbType.Object`                                               | `schema.type`                | `schema.type`         | `custom object`                                                          |
| `Object`                    | `OracleDbType.Array` \| `OracleDbType.Ref`                                             | `schema.type`                | none \| `schema.type` | Exception thrown                                                         |
| `Collection`                | `OracleDbType.Array | ``DbType.Object`                                                 | `schema.type`                | `schema.type`         | `custom object` \| `custom object[]` \| `.NET object[]` \| `PS object[]` |
| `Collection`                | `OracleDbType.Ref` \| `OracleDbType.Object`                                            | `schema.type`                | none \| `schema.type` | Exception thrown                                                         |
| `REF`                       | `DbType.Object` \| `OracleDbType.Object` \|` OracleDbType.Array`                       | `schema.type`                | none \| `schema.type` | Exception thrown                                                         |
| `REF`                       | `OracleDbType.Ref`                                                                     | `schema.type`                | none \| `schema.type` | `OracleRef`                                                              |

**See Also:**

- "[Parameter Binding](featOraCommand.md)"

- "[Typed OracleDataReader Accessors](featData.md)"

### Populating the DataSet with Oracle UDTs

The `DataSet` is a disconnected result set. With ADO.NET 2.0, both .NET types and provider-specific types can be used to populate the `DataSet`. This section describes the types used to populate the `DataSet` when the column is an Oracle UDT.

Table 3-26 lists the types that populate the `DataSet` column, based on the Oracle column type, the `ReturnProviderSpecificTypes` property of the `DataAdapter`, the existence of a custom type mapping, the `DataSet` column type, the `DataSet` column value, and the `DataSet` column null value.

Table 3-26 Types that Populate the DataSet with ADO.NET 2.0

| Oracle Column Type      | ReturnProvider- SpecificTypes Property | Custom Type Mappings | DataSet Column Type                                                                | DataSet Column Value                                | DataSet Column Null Value |
|:------------------------|:---------------------------------------|:---------------------|:-----------------------------------------------------------------------------------|:----------------------------------------------------|:--------------------------|
| `Object` / `Collection` | `False`/`True`                         | none                 | Exception thrown                                                                   | Exception thrown                                    | Exception thrown          |
| `Object` / `Collection` | `False`                                | schema.type          | `typeof(``custom type``)`                                                          | `custom object`                                     | `DbNull.Value`            |
| `Object` / `Collection` | `True`                                 | schema.type          | `typeof(``custom type``)`                                                          | `custom object`                                     | `custom object``.Null`    |
| `Collection`            | `False`                                | schema.type          | `typeof(``custom type[]``)`\| `typeof(``.NET type[]``)` \| `typeof(``PS type[]``)` | `.NET type[]` \| `PS object[]` \| `custom object[]` | `DbNull.Value`            |
| `Collection`            | `True`                                 | schema.type          | `typeof(``custom type[]``)`\| `typeof(``.NET type[]``)` \| `typeof(``PS type[]``)` | `.NET type[]` \| `PS object[]` \| `custom object[]` | `null`                    |
| `REF`                   | `False`                                | none \| schema.type  | `typeof(string)`                                                                   | `string`/HEX                                        | `DbNull.Value`            |
| `REF`                   | `True`                                 | none \| schema.type  | `typeof(OracleRef)`                                                                | `OracleRef`                                         | `OracleRef.Null`          |

### UDT Method Invocation

ODP.NET supports invocation of methods defined for a UDT on the database. This can be accomplished by doing the following:

1.  Set the `CommandType` as `CommandType.StoredProcedure`.

2.  Set the `CommandText` as `"``type_name.procedure_name``"`

3.  Execute the command using any of the `Execute` methods on the `OracleCommand` object.

For instance functions, the parameters are as follows:

- The first parameter must be the return value.

- The second parameter must be the UDT instance on which the instance method is invoked, which is the instance of the .NET custom object.

- Subsequent parameters are for the function.

For instance procedures, the first parameter must be the UDT instance.

For static methods, the UDT instance is not needed.

### Configuration Settings for Oracle UDTs

ODP.NET exposes two configuration settings to determine how ODP.NET handles Oracle UDTs.

- StatementCacheWithUdts

- UdtCacheSize

These configuration settings can be specified as machine-wide settings for a particular version of ODP.NET, using the registry key with the name that exists under `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE``\ODP.NET\``Assembly_Version`. The configuration settings specified in the registry can be overridden if an entry is created in the `machine.config` for .NET framework-wide settings, or in the `app.config` or `web.config` for application-specific settings.

**See Also:**

[Configuring Oracle Data Provider for .NET](InstallConfig.md) for details on configuring ODP.NET.

#### StatementCacheWithUdts

`StatementCacheWithUdts` specifies whether or not ODP.NET caches Oracle UDTs retrieved by a `SELECT` statement along with the statement when it is returned to the statement cache. Possible values are `1` - Yes (the default) or 0 - No.

For the value of 1, the Oracle UDTs are cached along with the statements. Therefore, the memory that contained the UDTs can be re-used; subsequent executions of the same statement do not require additional memory. This may result in an overall higher performance.

For the value of 0, ODP.NET frees the memory for the retrieved Oracle UDTs before the statement is returned to the statement cache. This may result in poorer performance because subsequent executions will require new memory allocations.

#### UdtCacheSize

`UdtCacheSize` specifies the size of the object cache for each connection that ODP.NET uses when retrieving and manipulating Oracle UDTs. The value for this setting must be specified in kilobytes (KB) with the default 4096KB, equivalent to 4 MB.

This configuration setting is used to determine how frequently the objects in the object cache will be purged (using an LRU approach) as the limit of the object cache size approaches.
