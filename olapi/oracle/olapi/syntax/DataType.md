Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](DataObject.md)
- [Next Class](DateExpression.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.olapi.syntax

## Class DataType

- java.lang.Object

- - oracle.olapi.syntax.DataType

<!-- -->

-

  ------------------------------------------------------------------------



      public final class DataType
      extends java.lang.Object

  An object that represents an Oracle Database data type without precision information. A `DataType` has a name and a category. An application gets an instance of this class by using one of the static constants, such as `DataType.NUMBER`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type   | Field and Description                                                                                                             |
    |---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `static int`        | `ANY_CATEGORY`<br>A constant that represents a category for any data type.                                                        |
    | `static DataType`   | `BINARY_DOUBLE`<br>A constant that represents the `BINARY DOUBLE` data type.                                                      |
    | `static DataType`   | `BINARY_FLOAT`<br>A constant that represents the `BINARY FLOAT` data type.                                                        |
    | `static DataType`   | `BLOB`<br>A constant that represents the `BLOB` data type.                                                                        |
    | `static int`        | `CASTABLE_TO_NUMBER_CATEGORY`<br>A constant that represents a category of data types that are castable to the `NUMBER` data type. |
    | `static DataType`   | `CHAR`<br>A constant that represents the `CHAR` data type.                                                                        |
    | `static DataType`   | `CLOB`<br>A constant that represents the `CLOB` data type.                                                                        |
    | `static int`        | `CLOB_CATEGORY`<br>A constant that represents a category of `CLOB` data types.                                                    |
    | `static DataType`   | `DATE`<br>A constant that represents the `DATE` data type.                                                                        |
    | `static int`        | `DATE_CATEGORY`<br>A constant that represents a category of `DATE` data types.                                                    |
    | `static int`        | `DATETIME_CATEGORY`<br>A constant that represents a category of `DATE` and `TIMESTAMP` data types.                                |
    | `static int`        | `DATETIME_OR_INTERVAL_CATEGORY`<br>A constant that represents a category of `DATE`, `TIMESTAMP`, and `INTERVAL` data types.       |
    | `static DataType`   | `DECIMAL`<br>A constant that represents the `DECIMAL` data type.                                                                  |
    | `static DataType`   | `DS_INTERVAL`<br>A constant that represents an `INTERVAL DAY TO SECOND` data type.                                                |
    | `static DataType`   | `FLOAT`<br>A constant that represents the `FLOAT` data type.                                                                      |
    | `static DataType`   | `INTEGER`<br>A constant that represents the `INTEGER` data type.                                                                  |
    | `static int`        | `INTERVAL_CATEGORY`<br>A constant that represents a category of `INTERVAL` data types.                                            |
    | `static int`        | `LITERAL_CATEGORY`<br>A constant that represents a category of literal data types.                                                |
    | `static DataType[]` | `LITERAL_DATA_TYPES`<br>A constant that represent an array of the literal data types.                                             |
    | `static DataType`   | `LOB`<br>A constant that represents the `LOB` data type.                                                                          |
    | `static int`        | `LOB_CATEGORY`<br>A constant that represents a category of `LOB` data types.                                                      |
    | `static DataType`   | `LONG`<br>A constant that represents the `LONG` data type.                                                                        |
    | `static int`        | `LONG_CATEGORY`<br>A constant that represents a category of `LONG` data types.                                                    |
    | `static DataType`   | `LONG_RAW`<br>A constant that represents the `LONG RAW` data type.                                                                |
    | `static DataType`   | `MLSLABEL`<br>A constant that represents the `MLSLABEL` data type.                                                                |
    | `static DataType`   | `NCHAR`<br>A constant that represents the `NCHAR` data type.                                                                      |
    | `static DataType`   | `NCLOB`<br>A constant that represents the `NCLOB` data type.                                                                      |
    | `static DataType`   | `NULL_TYPE`<br>A constant that represents a `null` data type.                                                                     |
    | `static DataType`   | `NUMBER`<br>A constant that represents the `NUMBER` data type.                                                                    |
    | `static int`        | `NUMBER_CATEGORY`<br>A constant that represents a category of number data types.                                                  |
    | `static DataType`   | `NVARCHAR2`<br>A constant that represents the `NVARCHAR2` data type.                                                              |
    | `static int`        | `OBJECT_CATEGORY`<br>A constant that represents the object category of data types.                                                |
    | `static DataType`   | `RAW`<br>A constant that represents the `RAW` data type.                                                                          |
    | `static int`        | `RAW_CATEGORY`<br>A constant that represents a category of `RAW` data types.                                                      |
    | `static DataType`   | `ROWID`<br>A constant that represents the `ROWID` data type.                                                                      |
    | `static int`        | `ROWID_CATEGORY`<br>A constant that represents a category of `ROWID` data types.                                                  |
    | `static int`        | `TEXT_CATEGORY`<br>A constant that represents a category of text literal and `CLOB` data types.                                   |
    | `static int`        | `TEXT_LITERAL_CATEGORY`<br>A constant that represents category of text data types.                                                |
    | `static int`        | `TEXT_OR_NUMBER_CATEGORY`<br>A constant that represents a category of text literal and `NUMBER` data types.                       |
    | `static DataType`   | `TIMESTAMP`<br>A constant that represents the `TIMESTAMP` data type.                                                              |
    | `static int`        | `TIMESTAMP_CATEGORY`<br>A constant that represents a category of `TIMESTAMP` data types.                                          |
    | `static DataType`   | `TIMESTAMP_WITH_LOCAL_TIME_ZONE`<br>A constant that represents the `TIMESTAMP WITH LOCAL TIME ZONE` data type.                    |
    | `static DataType`   | `TIMESTAMP_WITH_TIME_ZONE`<br>A constant that represents the `TIMESTAMP WITH TIME ZONE` data type.                                |
    | `static DataType`   | `VARCHAR2`<br>A constant that represents the `VARCHAR2` data type.                                                                |
    | `static int`        | `XML_FORMAT_CATEGORY`<br>A constant that represents the XML format category of data types.                                        |
    | `static int`        | `XML_TYPE_CATEGORY`<br>A constant that represents the XML type category of data types.                                            |
    | `static DataType`   | `XMLFORMAT`<br>A constant that represents the `XMLFormat` data type.                                                              |
    | `static DataType`   | `XMLTYPE`<br>A constant that represents the `XMLTYPE` data type.                                                                  |
    | `static DataType`   | `YM_INTERVAL`<br>A constant that represents an `INTERVAL YEAR TO MONTH` data type.                                                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                           |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static DataType`               | `getDataType``(java.lang.String name)`<br>Gets the `DataType` that has the specified name.                                                       |
    | `java.lang.String`              | `getName``()`<br>Gets the name of this `DataType`.                                                                                               |
    | `boolean`                       | `matchesCategory``(int category)`<br>Indicates whether or not the category of this `DataType` matches the specified category.                    |
    | `boolean`                       | `matchesCategory``(int category, boolean allowCast)`<br>Indicates whether or not the category of this `DataType` matches the specified category. |
    | [`SQLDataType`](SQLDataType.md) | `toSQLDataType``()`<br>Gets the `SQLDataType` for this `DataType`.                                                                               |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TEXT_LITERAL_CATEGORY

          public static final int TEXT_LITERAL_CATEGORY

      A constant that represents category of text data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NUMBER_CATEGORY

          public static final int NUMBER_CATEGORY

      A constant that represents a category of number data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INTERVAL_CATEGORY

          public static final int INTERVAL_CATEGORY

      A constant that represents a category of `INTERVAL` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TIMESTAMP_CATEGORY

          public static final int TIMESTAMP_CATEGORY

      A constant that represents a category of `TIMESTAMP` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATE_CATEGORY

          public static final int DATE_CATEGORY

      A constant that represents a category of `DATE` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OBJECT_CATEGORY

          public static final int OBJECT_CATEGORY

      A constant that represents the object category of data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLOB_CATEGORY

          public static final int CLOB_CATEGORY

      A constant that represents a category of `CLOB` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LOB_CATEGORY

          public static final int LOB_CATEGORY

      A constant that represents a category of `LOB` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RAW_CATEGORY

          public static final int RAW_CATEGORY

      A constant that represents a category of `RAW` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LONG_CATEGORY

          public static final int LONG_CATEGORY

      A constant that represents a category of `LONG` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ROWID_CATEGORY

          public static final int ROWID_CATEGORY

      A constant that represents a category of `ROWID` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XML_FORMAT_CATEGORY

          public static final int XML_FORMAT_CATEGORY

      A constant that represents the XML format category of data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XML_TYPE_CATEGORY

          public static final int XML_TYPE_CATEGORY

      A constant that represents the XML type category of data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ANY_CATEGORY

          public static final int ANY_CATEGORY

      A constant that represents a category for any data type.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CASTABLE_TO_NUMBER_CATEGORY

          public static final int CASTABLE_TO_NUMBER_CATEGORY

      A constant that represents a category of data types that are castable to the `NUMBER` data type.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATETIME_CATEGORY

          public static final int DATETIME_CATEGORY

      A constant that represents a category of `DATE` and `TIMESTAMP` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATETIME_OR_INTERVAL_CATEGORY

          public static final int DATETIME_OR_INTERVAL_CATEGORY

      A constant that represents a category of `DATE`, `TIMESTAMP`, and `INTERVAL` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEXT_CATEGORY

          public static final int TEXT_CATEGORY

      A constant that represents a category of text literal and `CLOB` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LITERAL_CATEGORY

          public static final int LITERAL_CATEGORY

      A constant that represents a category of literal data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEXT_OR_NUMBER_CATEGORY

          public static final int TEXT_OR_NUMBER_CATEGORY

      A constant that represents a category of text literal and `NUMBER` data types.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NULL_TYPE

          public static final DataType NULL_TYPE

      A constant that represents a `null` data type.

    <!-- -->

    - #### NUMBER

          public static final DataType NUMBER

      A constant that represents the `NUMBER` data type.

    <!-- -->

    - #### BINARY_FLOAT

          public static final DataType BINARY_FLOAT

      A constant that represents the `BINARY FLOAT` data type.

    <!-- -->

    - #### BINARY_DOUBLE

          public static final DataType BINARY_DOUBLE

      A constant that represents the `BINARY DOUBLE` data type.

    <!-- -->

    - #### FLOAT

          public static final DataType FLOAT

      A constant that represents the `FLOAT` data type.

    <!-- -->

    - #### INTEGER

          public static final DataType INTEGER

      A constant that represents the `INTEGER` data type.

    <!-- -->

    - #### DECIMAL

          public static final DataType DECIMAL

      A constant that represents the `DECIMAL` data type.

    <!-- -->

    - #### CHAR

          public static final DataType CHAR

      A constant that represents the `CHAR` data type.

    <!-- -->

    - #### NCHAR

          public static final DataType NCHAR

      A constant that represents the `NCHAR` data type.

    <!-- -->

    - #### VARCHAR2

          public static final DataType VARCHAR2

      A constant that represents the `VARCHAR2` data type.

    <!-- -->

    - #### NVARCHAR2

          public static final DataType NVARCHAR2

      A constant that represents the `NVARCHAR2` data type.

    <!-- -->

    - #### CLOB

          public static final DataType CLOB

      A constant that represents the `CLOB` data type.

    <!-- -->

    - #### NCLOB

          public static final DataType NCLOB

      A constant that represents the `NCLOB` data type.

    <!-- -->

    - #### DATE

          public static final DataType DATE

      A constant that represents the `DATE` data type.

    <!-- -->

    - #### TIMESTAMP

          public static final DataType TIMESTAMP

      A constant that represents the `TIMESTAMP` data type.

    <!-- -->

    - #### TIMESTAMP_WITH_LOCAL_TIME_ZONE

          public static final DataType TIMESTAMP_WITH_LOCAL_TIME_ZONE

      A constant that represents the `TIMESTAMP WITH LOCAL TIME ZONE` data type.

    <!-- -->

    - #### TIMESTAMP_WITH_TIME_ZONE

          public static final DataType TIMESTAMP_WITH_TIME_ZONE

      A constant that represents the `TIMESTAMP WITH TIME ZONE` data type.

    <!-- -->

    - #### YM_INTERVAL

          public static final DataType YM_INTERVAL

      A constant that represents an `INTERVAL YEAR TO MONTH` data type.

    <!-- -->

    - #### DS_INTERVAL

          public static final DataType DS_INTERVAL

      A constant that represents an `INTERVAL DAY TO SECOND` data type.

    <!-- -->

    - #### MLSLABEL

          public static final DataType MLSLABEL

      A constant that represents the `MLSLABEL` data type.

    <!-- -->

    - #### RAW

          public static final DataType RAW

      A constant that represents the `RAW` data type.

    <!-- -->

    - #### LONG_RAW

          public static final DataType LONG_RAW

      A constant that represents the `LONG RAW` data type.

    <!-- -->

    - #### LONG

          public static final DataType LONG

      A constant that represents the `LONG` data type.

    <!-- -->

    - #### ROWID

          public static final DataType ROWID

      A constant that represents the `ROWID` data type.

    <!-- -->

    - #### LOB

          public static final DataType LOB

      A constant that represents the `LOB` data type.

    <!-- -->

    - #### BLOB

          public static final DataType BLOB

      A constant that represents the `BLOB` data type.

    <!-- -->

    - #### XMLTYPE

          public static final DataType XMLTYPE

      A constant that represents the `XMLTYPE` data type.

    <!-- -->

    - #### XMLFORMAT

          public static final DataType XMLFORMAT

      A constant that represents the `XMLFormat` data type.

    <!-- -->

    - #### LITERAL_DATA_TYPES

          public static final DataType[] LITERAL_DATA_TYPES

      A constant that represent an array of the literal data types.

  <!-- -->

  - ### Method Detail

    - #### getName

          public final java.lang.String getName()

      Gets the name of this `DataType`.
      Returns:
      A `String` that contains the name of this `DataType`.

    <!-- -->

    - #### matchesCategory

          public boolean matchesCategory(int category)

      Indicates whether or not the category of this `DataType` matches the specified category.
      Parameters:
      `category` - One of the category constant fields of this class, such as `DataType.NUMBER_CATEGORY`.

      Returns:
      A `boolean` that is `true` if the specified categroy matches the category of this `DataType` or is `false` otherwise.

    <!-- -->

    - #### matchesCategory

          public boolean matchesCategory(int category,
                                         boolean allowCast)

      Indicates whether or not the category of this `DataType` matches the specified category.
      Parameters:
      `category` - One of the category constant fields of this class, such as `DataType.NUMBER_CATEGORY`.

      `allowCast` - If true, check to see if the provided datatype can be cast to the expected datatype

      Returns:
      A `boolean` that is `true` if the specified categroy matches the category of this `DataType` or is `false` otherwise.

    <!-- -->

    - #### getDataType

          public static final DataType getDataType(java.lang.String name)

      Gets the `DataType` that has the specified name.
      Parameters:
      `name` - A `String` that contains the name of a `DataType`, such as `TIMESTAMP`.

      Returns:
      A `DataType` with the specified name.

    <!-- -->

    - #### toSQLDataType

          public final SQLDataType toSQLDataType()

      Gets the `SQLDataType` for this `DataType`.
      Returns:
      The `SQLDataType` for this `DataType`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DataObject.md)
- [Next Class](DateExpression.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
