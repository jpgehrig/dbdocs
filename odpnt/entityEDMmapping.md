The ODP.NET manifest file describes the primitive types, such as `VARCHAR2` and `Number`, and the Entity Data Model (EDM) types, such as `string` and `Int32`, that they map to. It also includes the facets for each EDM type.

ODP.NET does not support Time literals and canonical functions related to the Time type.

Oracle considers both `NULL` and empty strings to be `NULL` strings and are considered to be equal. Operations, such as `Equals(), Length(),` and `Trim() `on such strings will result in a `NULL` string.

Table 4-1 maps the Oracle data types to their corresponding EDM types. The table also includes details about provider type attributes and the EDM type facets associated with each Oracle data type.

Table 4-1 Mapping of Oracle Data Types and EDM Types

| Oracle Data Types                                                                                                                                              | EDM Types(Primitive-TypeKind) | Provider Type Attributes: Name and Value                   | EDM Type Facets                                    |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------|:-----------------------------------------------------------|:---------------------------------------------------|
| `Bfile`                                                                                                                                                        | `Binary`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for Bfile                          |
| `Binary_Double`                                                                                                                                                | `Double`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Binary_Float`                                                                                                                                                 | `Single`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Binary_Integer`                                                                                                                                               | `Int32`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Blob`                                                                                                                                                         | `Binary`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for Blob                           |
| `Char`                                                                                                                                                         | `String`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Char                           |
| `Clob`                                                                                                                                                         | `String`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for Clob                           |
| `Date`                                                                                                                                                         | `DateTime`                    | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Date                           |
| `Float`                                                                                                                                                        | `Decimal`                     | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Float                          |
| `Int`                                                                                                                                                          | `Int32`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Interval Day To Second`                                                                                                                                       | `Decimal`                     | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Interval Day To Second         |
| `Interval Year To Month`                                                                                                                                       | `Decimal`                     | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Interval Year To Month         |
| `Long`                                                                                                                                                         | `String`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for Long                           |
| `Long Raw`                                                                                                                                                     | `Binary`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for Long Raw                       |
| `NChar`                                                                                                                                                        | `String`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for NChar                          |
| `NClob`                                                                                                                                                        | `String`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for NClob                          |
| `Nested Table`                                                                                                                                                 |                               | Not Applicable                                             | Not Applicable and Not Supported                   |
| `Number(1,0)`<br>`Number(2,0)`<br>`Number(3,0)`<br>`Number(4,0)`<br>`Number(5,0)`                                                                              | `Int16`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Number(6,0)`<br>`Number(7,0)`<br>`Number(8,0)`<br>`Number(9,0)`<br>`Number(10,0)`                                                                             | `Int32`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Number(11,0)`<br>`Number(12,0)`<br>`Number(13,0)`<br>`Number(14,0)`<br>`Number(15,0)`<br>`Number(16,0)`<br>`Number(17,0)`<br>`Number(18,0)`<br>`Number(19,0)` | `Int64`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Number`<br>(all other cases)                                                                                                                                  | `Decimal`                     | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Number                         |
| `NVarchar2`                                                                                                                                                    | `String`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for NVarchar2                      |
| `Object`                                                                                                                                                       |                               | Not Applicable                                             | Not Applicable and Not Supported                   |
| `Raw`                                                                                                                                                          | `Binary`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Raw                            |
| `Raw(16)`                                                                                                                                                      | `Guid`                        | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Ref`                                                                                                                                                          |                               | Not Applicable                                             | Not Applicable and Not Supported                   |
| `ROWID`                                                                                                                                                        | `String`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for ROWID                          |
| `Smallint`                                                                                                                                                     | `Int16`                       | • `Equal Comparable: True`<br>• `Order Comparable: True`   | Not Applicable                                     |
| `Timestamp`                                                                                                                                                    | `DateTime`                    | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Timestamp                      |
| `Timestamp with`<br>`Local Time Zone`                                                                                                                          | `DateTime`                    | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Timestamp with Local Time Zone |
| `Timestamp with`<br>`Time Zone`                                                                                                                                | `DateTimeOffset`              | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Timestamp with Time Zone       |
| `UROWID`<br>(size)                                                                                                                                             | `Binary`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for UROWID                         |
| `Varchar2`                                                                                                                                                     | `String`                      | • `Equal Comparable: True`<br>• `Order Comparable: True`   | EDM Type Facets for Varchar2                       |
| `VArray`                                                                                                                                                       |                               | Not Applicable                                             | Not Applicable and Not Supported                   |
| `XMLType`                                                                                                                                                      | `String`                      | • `Equal Comparable: False`<br>• `Order Comparable: False` | EDM Type Facets for XMLType                        |

### EDM Type Facets

The following sections enumerate the EDM type facets for the preceding Oracle data types. The first column of each table displays the EDM type facet names for the Oracle data type. Subsequent columns list the facet attribute names and displays their respective values.

#### EDM Type Facets for Bfile

Table 4-2 EDM Type Facets for Bfile

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483648`<br>`Constant`: `True` |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for Blob

Table 4-3 EDM Type Facets for Blob

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483648`<br>`Constant`: `True` |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for Char

Table 4-4 EDM Type Facets for Char

| Facet Name    | Attributes Name and Value                                                            |
|:--------------|:-------------------------------------------------------------------------------------|
| `MaxLength`   | `Minimum`: `1`<br>`Maximum`: `2000`<br>`DefaultValue`: `2000`<br>`Constant`: `False` |
| `Unicode`     | `DefaultValue`: `False`<br>`Constant`: `True`                                        |
| `FixedLength` | `DefaultValue`: `True`<br>`Constant`: `True`                                         |

#### EDM Type Facets for Clob

Table 4-5 EDM Type Facets for Clob

| Facet Name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483647`<br>`Constant`: `True` |
| `Unicode`     | `DefaultValue`: `False`<br>`Constant`: `True`      |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for Date

Table 4-6 EDM Type Facets for Date

| Facet Name  | Attributes Name and Value                 |
|:------------|:------------------------------------------|
| `Precision` | `Constant`: `True`<br>`DefaultValue`: `0` |

#### EDM Type Facets for Float

Table 4-7 EDM Type Facets for Float

| Facet name  | Attributes Name and Value                                                        |
|:------------|:---------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `0`<br>`Maximum`: `126`<br>`DefaultValue`: `0`<br>`Constant`: `False` |
| `Scale`     | `Minimum`: `0`<br>`Maximum`: `38`<br>`DefaultValue`: `0`<br>`Constant`: `False`  |

#### EDM Type Facets for Interval Day To Second

Table 4-8 EDM Type Facets for Interval Day To Second

| Facet name  | Attributes Name and Value                                                          |
|:------------|:-----------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `1`<br>`Maximum`: `251`<br>`DefaultValue`: `251`<br>`Constant`: `False` |
| `Scale`     | `Minimum`: `0`<br>`Maximum`: `9`<br>`DefaultValue`: `0`<br>`Constant`: `False`     |

**Note:**

EDM types do not support `TimeSpan`.

Use `Decimal` to represent the total number of seconds. An application can obtain a `TimeSpan` by using the `TimeSpan.FromSeconds` static method.

#### EDM Type Facets for Interval Year To Month

Table 4-9 EDM Type Facets for Interval Year To Month

| Facet name  | Attributes Name and Value                                                          |
|:------------|:-----------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `1`<br>`Maximum`: `250`<br>`DefaultValue`: `250`<br>`Constant`: `False` |
| `Scale`     | `Minimum`: `0`<br>`Maximum`: `9`<br>`DefaultValue`: `0`<br>`Constant`: `False`     |

#### EDM Type Facets for Long

Table 4-10 EDM Type Facets for Long

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483647`<br>`Constant`: `True` |
| `Unicode`     | `DefaultValue`: `False`<br>`Constant`: `True`      |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for Long Raw

Table 4-11 EDM Type Facets for Long Raw

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483647`<br>`Constant`: `True` |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for NChar

Table 4-12 EDM Type Facets for NChar

| Facet name    | Attributes Name and Value                                                            |
|:--------------|:-------------------------------------------------------------------------------------|
| `MaxLength`   | `Minimum`: `1`<br>`Maximum`: `1000`<br>`DefaultValue`: `1000`<br>`Constant`: `False` |
| `Unicode`     | `DefaultValue`: `True`<br>`Constant`: `True`                                         |
| `FixedLength` | `DefaultValue`: `True`<br>`Constant`: `True`                                         |

**Note:**

For `NChar,` the actual data is subject to the maximum byte limit of 2000.

The value of 1000 for `Maximum` and `DefaultValue` allows the EDM wizard to display columns of `NCHAR(1000)`, where 1000 is the maximum number of characters allowed in DDL.

#### EDM Type Facets for NClob

Table 4-13 EDM Type Facets for NClob

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483647`<br>`Constant`: `True` |
| `Unicode`     | `DefaultValue`: `True`<br>`Constant`: `True`       |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |

#### EDM Type Facets for Number

Table 4-14 EDM Type Facets for Number

| Facet name  | Attributes Name and Value                                                        |
|:------------|:---------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `1`<br>`Maximum`: `38`<br>`DefaultValue`: `38`<br>`Constant`: `False` |
| `Scale`     | `Minimum`: `0`<br>`Maximum`: `38`<br>`DefaultValue`: `0`<br>`Constant`: `False`  |

#### EDM Type Facets for NVarchar2

Table 4-15 EDM Type Facets for NVarchar2

| Facet name    | Attributes Name and Value                                                            |
|:--------------|:-------------------------------------------------------------------------------------|
| `MaxLength`   | `Minimum`: `1`<br>`Maximum`: `2000`<br>`DefaultValue`: `2000`<br>`Constant`: `False` |
| `Unicode`     | `DefaultValue`: `True`<br>`Constant`: `True`                                         |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`                                        |

**Note:**

For `NVARCHAR2,` the actual data is subject to the maximum byte limit of 4000.

The value of 2000 for `Maximum` and `DefaultValue` allows the EDM wizard to display columns of `NVARCHAR2(2000)`, where 2000 is the maximum number of characters allowed in DDL.

#### EDM Type Facets for Raw

Table 4-16 EDM Type Facets for Raw

| Facet name    | Attributes Name and Value                                  |
|:--------------|:-----------------------------------------------------------|
| `MaxLength`   | `Minimum`: `1`<br>`Maximum`: `2000`<br>`Constant`: `False` |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`              |

#### EDM Type Facets for ROWID

Table 4-17 EDM Type Facets for ROWID

| Facet name    | Attributes Name and Value                     |
|:--------------|:----------------------------------------------|
| `MaxLength`   | `DefaultValue`: `18`<br>`Constant`: `True`    |
| `Unicode`     | `DefaultValue`: `False`<br>`Constant`: `True` |
| `FixedLength` | `DefaultValue`: `True`<br>`Constant`: `True`  |

#### EDM Type Facets for Timestamp

Table 4-18 EDM Type Facets for Timestamp

| Facet name  | Attributes Name and Value                                                      |
|:------------|:-------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `0`<br>`Maximum`: `9`<br>`DefaultValue`: `6`<br>`Constant`: `False` |

#### EDM Type Facets for Timestamp with Local Time Zone

Table 4-19 EDM Type Facets for Timestamp with Local Time Zone

| Facet name  | Attributes Name and Value                                                      |
|:------------|:-------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `0`<br>`Maximum`: `9`<br>`DefaultValue`: `6`<br>`Constant`: `False` |

#### EDM Type Facets for Timestamp with Time Zone

Table 4-20 EDM Type Facets for Timestamp with Time Zone

| Facet name  | Attributes Name and Value                                                      |
|:------------|:-------------------------------------------------------------------------------|
| `Precision` | `Minimum`: `0`<br>`Maximum`: `9`<br>`DefaultValue`: `6`<br>`Constant`: `False` |

#### EDM Type Facets for UROWID

Table 4-21 EDM Type Facets for UROWID

| Facet name    | Attributes Name and Value                    |
|:--------------|:---------------------------------------------|
| `MaxLength`   | `DefaultValue`: `4000`<br>`Constant`: `True` |
| `FixedLength` | `DefaultValue`: `True`<br>`Constant`: `True` |

#### EDM Type Facets for Varchar2

Table 4-22 EDM Type Facets for Varchar2

| Facet name    | Attributes Name and Value                                                            |
|:--------------|:-------------------------------------------------------------------------------------|
| `MaxLength`   | `Minimum`: `1`<br>`Maximum`: `4000`<br>`DefaultValue`: `4000`<br>`Constant`: `False` |
| `Unicode`     | `DefaultValue`: `False`<br>`Constant`: `True`                                        |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`                                        |

#### EDM Type Facets for XMLType

Table 4-23 EDM Type Facets for XMLType

| Facet name    | Attributes Name and Value                          |
|:--------------|:---------------------------------------------------|
| `MaxLength`   | `DefaultValue`: `2147483647`<br>`Constant`: `True` |
| `Unicode`     | `DefaultValue`: `True`<br>`Constant`: `True`       |
| `FixedLength` | `DefaultValue`: `False`<br>`Constant`: `True`      |
