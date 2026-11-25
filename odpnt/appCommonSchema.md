The common schema collections are available for all .NET Framework managed providers. ODP.NET supports the same common schema collections.

- MetaDataCollections

- DataSourceInformation

- DataTypes

- Restrictions

- ReservedWords

**See Also:**

"Common Schema Collections" in the [MSDN Library](https://msdn.microsoft.com/en-us/library/ms254501(v=vs.110).aspx)

### MetaDataCollections

Table A-1 is a list of metadata collections that is available from the data source, such as tables, columns, indexes, and stored procedures.

Table A-1 MetaDataCollections

| Column Name               | Data Type | Description                                                                |
|:--------------------------|:----------|:---------------------------------------------------------------------------|
| `CollectionName`          | `string`  | The name of the collection passed to the `GetSchema` method for retrieval. |
| `NumberOfRestrictions`    | `int`     | Number of restrictions specified for the named collection.                 |
| `NumberOfIdentifierParts` | `int`     | Number of parts in the composite identifier/database object name.          |

### DataSourceInformation

Table A-2 lists `DataSourceInformation` information which may include these columns and possibly others.

Table A-2 DataSource Information

| Columns                               | Data Type                 | Description                                                                                                                                                                       |
|:--------------------------------------|:--------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CompositeIdentifierSeparatorPattern` | `string`                  | Separator for multipart names: `@` `|` `\` .                                                                                                                                      |
| `DataSourceProductName`               | `string`                  | Database name: Oracle                                                                                                                                                             |
| `DataSourceProductVersion`            | `string`                  | Database version. Note that this is the version of the database instance currently being accessed by `DbConnection`.                                                              |
| `DataSourceProductVersionNormalized`  | `string`                  | A normalized DataSource version for easier comparison between different versions. For example:<br>DataSource Version: 10.2.0.1.0<br>Normalized DataSource Version: 10.02.00.01.00 |
| `GroupByBehavior`                     | `GroupByBehavior`         | An enumeration that indicates the relationship between the columns in a `GROUP` `BY` clause and the non-aggregated columns in a select list.                                      |
| `IdentifierPattern`                   | `string`                  | Format for a valid identifier.                                                                                                                                                    |
| `IdentifierCase`                      | `IdentifierCase`          | An enumeration that specifies whether or not to treat non-quoted identifiers as case sensitive.                                                                                   |
| `OrderByColumnsInSelect`              | `bool`                    | A boolean that indicates whether or not the select list must contain the columns in an `ORDER` `BY` clause.                                                                       |
| `ParameterMarkerFormat`               | `string`                  | A string indicating whether or not parameter markers begin with a special character.                                                                                              |
| `ParameterMarkerPattern`              | `string`                  | The format of a parameter marker.                                                                                                                                                 |
| `ParameterNameMaxLength`              | `int`                     | Maximum length of a parameter.                                                                                                                                                    |
| `ParameterNamePattern`                | `string`                  | The format for a valid parameter name.                                                                                                                                            |
| `QuotedIdentifierPattern`             | `string`                  | The format of a quoted identifier.                                                                                                                                                |
| `QuotedIdentifierCase`                | `IdentifierCase`          | An enumeration that specifies whether or not to treat quote identifiers as case sensitive.                                                                                        |
| `StringLiteralPattern`                | `string`                  | The format for a string literal.                                                                                                                                                  |
| `SupportedJoinOperators`              | `SupportedJoin Operators` | An enumeration indicating the types of SQL join statements supported by the data source.                                                                                          |

### DataTypes

Table A-3 lists DataTypes Collection information which may include these columns and possibly others.

**Note:**

As an example, the description column includes complete information for the `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` data type.

Table A-3 Data Types

| ColumnName              | Data Type | Description                                                                                                                                                                                      |
|:------------------------|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TypeName`              | `string`  | The provider-specific data type name.<br>Example: `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`                                                                                                       |
| `ProviderDbType`        | `int`     | The provider-specific type value.<br>Example: `124`                                                                                                                                              |
| `ColumnSize`            | `long`    | The length of a non-numeric column or parameter.<br>Example:`27`                                                                                                                                 |
| `CreateFormat`          | `string`  | A format string that indicates how to add this column to a DDL statement.<br>Example: `TIMESTAMP({0}` `WITH` `LOCAL` `TIME` `ZONE)`                                                              |
| `CreateParameters`      | `string`  | The parameters specified to create a column of this data type.<br>Example: 8                                                                                                                     |
| `DataType`              | `string`  | The .NET type for the data type.<br>Example:` System.DateTime`                                                                                                                                   |
| `IsAutoIncrementable`   | `bool`    | A boolean value that indicates whether or not this data type can be auto-incremented.<br>Example: `false`                                                                                        |
| `IsBestMatch`           | `bool`    | A boolean value that indicates whether or not this data type is the best match to values in the `DataType` column.<br>Example: `false`                                                           |
| `IsCaseSensitive`       | `bool`    | A boolean value that indicates whether or not this data type is case-sensitive.<br>Example: `false`                                                                                              |
| `IsFixedLength`         | `bool`    | A boolean value that indicates whether or not this data type has a fixed length.<br>Example: `true`                                                                                              |
| `IsFixedPrecisionScale` | `bool`    | A boolean value that indicates whether or not this data type has a fixed precision and scale.<br>Example: `false`                                                                                |
| `IsLong`                | `bool`    | A boolean value that indicates whether or not this data type contains very long data.<br>Example: `false`                                                                                        |
| `IsNullable`            | `bool`    | A boolean value that indicates whether or not this data type is nullable.<br>Example: `true`                                                                                                     |
| `IsSearchable`          | `bool`    | A boolean value that indicates whether or not the data type can be used in a `WHERE` clause with any operator, except the `LIKE` predicate.<br>Example: `true`                                   |
| `IsSearchableWithLike`  | `bool`    | A boolean value that indicates whether or not this data type can be used with the `LIKE` predicate.<br>Example: `false`                                                                          |
| `IsUnsigned`            | `bool`    | A boolean value that indicates whether or not the data type is unsigned.                                                                                                                         |
| `MaximumScale`          | `short`   | The maximum number of digits allowed to the right of the decimal point.                                                                                                                          |
| `MinimumScale`          | `short`   | The minimum number of digits allowed to the right of the decimal point.                                                                                                                          |
| `IsConcurrencyType`     | `bool`    | A boolean value that indicates whether or not the database updates the data type every time the row is changed and the value of the column differs from all previous values.<br>Example: `false` |
| `MinimumVersion`        | `String`  | The earliest version of the database that can be used.<br>Example:`09.00.00.00.00`                                                                                                               |
| `IsLiteralSupported`    | `bool`    | A boolean value that indicates whether or not the data type can be expressed as a literal.<br>Example: `true`                                                                                    |
| `LiteralPrefix`         | `string`  | The prefix of a specified literal.<br>Example: `TO_TIMESTAMP_TZ('`                                                                                                                               |
| `LiteralSuffix`         | `string`  | The suffix of a specified literal.<br>Example: `','YYYY-MM-DD HH24:MI:SS.FF')`                                                                                                                   |

### Restrictions

Table A-4 lists Restrictions, including the following columns.

Table A-4 Restrictions

| ColumnName          | Data Type | Description                                              |
|:--------------------|:----------|:---------------------------------------------------------|
| `CollectionName`    | `string`  | The collection that the restrictions apply to.           |
| `RestrictionName`   | `string`  | The restriction name.                                    |
| `RestrictionNumber` | `int`     | A number that indicates the location of the restriction. |

### ReservedWords

The `ReservedWords` collection exposes information about the words that are reserved by the database currently connected to ODP.NET.

Table A-5 lists the ReservedWords Collection.

Table A-5 ReservedWords

| ColumnName     | Data Type | Description                      |
|:---------------|:----------|:---------------------------------|
| `ReservedWord` | `string`  | Provider-specific reserved words |
