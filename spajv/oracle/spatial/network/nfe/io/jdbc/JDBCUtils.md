Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JdbcDataSource.md)
- [Next Class](NFEAbstractDataSource.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc

## Class JDBCUtils

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.JDBCUtils

<!-- -->

-

  ------------------------------------------------------------------------



      public class JDBCUtils
      extends java.lang.Object

  Utilities used by NFE to execute queries and perform common operations.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `JDBCUtils``()`             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                                                                                                   |
    |-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static <T> java.lang.String` | `createInSQLExpression``(java.lang.String column, java.util.Collection<java.lang.Long> elements, boolean stringType)`<br>Creates a SQL IN expression of the form "column IN (elements)" taking care of the maximum number of elements supported in an in expression (1000).              |
    | `static void`                 | `createSequence``(java.sql.Connection conn, java.lang.String sequenceName, long initialValue, int increment)`<br>Creates a sequence.                                                                                                                                                     |
    | `static java.lang.String`     | `createSequenceForTable``(java.sql.Connection conn, java.lang.String tableName, long initialValue, int increment)`<br>Creates a sequence for a table, the name of the sequence will be the concatenation of the table name and \_ID_SEQ.                                                 |
    | `static void`                 | `deleteTable``(java.sql.Connection conn, java.lang.String tableName)`<br>Drops the table.                                                                                                                                                                                                |
    | `static java.lang.Object`     | `getResultSetColumnValue``(java.sql.ResultSet resultSet, java.lang.String columnName, `[`NFEAttributeType`](../../model/feature/NFEAttributeType.md)` expectedType)`<br>Gets the resultSet column value of the specified column, the resultSet will get the value depending on the type. |
    | `static long`                 | `getSequenceNextValue``(java.sql.Connection conn, java.lang.String seqName)`<br>Retrieves the next value from a given sequence name.                                                                                                                                                     |
    | `static long[]`               | `getSequenceNextValues``(java.sql.Connection conn, java.lang.String seqName, int valuesCount)`<br>Retrieves the next values from a given sequence name.                                                                                                                                  |
    | `static boolean`              | `tableExists``(java.sql.Connection conn, java.lang.String tableName)`<br>Returns true if a table with the specified name already exists, false otherwise.                                                                                                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JDBCUtils

          public JDBCUtils()

  <!-- -->

  - ### Method Detail

    - #### getSequenceNextValue

          public static long getSequenceNextValue(java.sql.Connection conn,
                                                  java.lang.String seqName)
                                           throws NFEIOException,
                                                  java.sql.SQLException

      Retrieves the next value from a given sequence name.
      Parameters:
      `conn` - connection

      `seqName` - sequence Name

      Returns:
      next sequence value

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

      [`NFEIOException`](../NFEIOException.md)

    <!-- -->

    - #### getSequenceNextValues

          public static long[] getSequenceNextValues(java.sql.Connection conn,
                                                     java.lang.String seqName,
                                                     int valuesCount)
                                              throws java.sql.SQLException

      Retrieves the next values from a given sequence name.
      Parameters:
      `conn` - connection

      `seqName` - sequence Name

      `valuesCount` - number of values to retrieve

      Returns:
      next sequence values

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

    <!-- -->

    - #### createSequenceForTable

          public static java.lang.String createSequenceForTable(java.sql.Connection conn,
                                                                java.lang.String tableName,
                                                                long initialValue,
                                                                int increment)
                                                         throws NFEIOException,
                                                                java.sql.SQLException

      Creates a sequence for a table, the name of the sequence will be the concatenation of the table name and \_ID_SEQ.
      Parameters:
      `conn` - connection

      `tableName` - table name

      `initialValue` - initial value of the sequence

      `increment` - sequence increment

      Returns:
      sequence name

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

      [`NFEIOException`](../NFEIOException.md)

    <!-- -->

    - #### createInSQLExpression

          public static <T> java.lang.String createInSQLExpression(java.lang.String column,
                                                                   java.util.Collection<java.lang.Long> elements,
                                                                   boolean stringType)

      Creates a SQL IN expression of the form "column IN (elements)" taking care of the maximum number of elements supported in an in expression (1000).
      Parameters:
      `column` - column name

      `elements` - elements to add to SQL IN expression

      `stringType` - true if the elements in the collection are strings false otherwise. If the elements are strings the quotes will be added

      Returns:
      one IN expression of the form "column IN (elements)" or two or more IN expressions of the form "column IN (elements 0 ....N ) OR column IN (elements N....M) .... OR column IN (elements X.....Y)"

    <!-- -->

    - #### getResultSetColumnValue

          public static java.lang.Object getResultSetColumnValue(java.sql.ResultSet resultSet,
                                                                 java.lang.String columnName,
                                                                 NFEAttributeType expectedType)
                                                          throws java.sql.SQLException

      Gets the resultSet column value of the specified column, the resultSet will get the value depending on the type.
      Parameters:
      `resultSet` - resultSet

      `columnName` - column

      `expectedType` - expected type

      Returns:
      column value

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

    <!-- -->

    - #### createSequence

          public static void createSequence(java.sql.Connection conn,
                                            java.lang.String sequenceName,
                                            long initialValue,
                                            int increment)
                                     throws NFEIOException,
                                            java.sql.SQLException

      Creates a sequence.
      Parameters:
      `conn` - connection

      `sequenceName` - name of the sequence

      `initialValue` - initial value of the sequence

      `increment` - sequence increment

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

      [`NFEIOException`](../NFEIOException.md)

    <!-- -->

    - #### tableExists

          public static boolean tableExists(java.sql.Connection conn,
                                            java.lang.String tableName)
                                     throws java.sql.SQLException

      Returns true if a table with the specified name already exists, false otherwise.
      Parameters:
      `conn` - connection

      `tableName` - table name

      Returns:
      true if a table with the specified name already exists, false otherwise

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

    <!-- -->

    - #### deleteTable

          public static void deleteTable(java.sql.Connection conn,
                                         java.lang.String tableName)
                                  throws NFEIOException,
                                         java.sql.SQLException

      Drops the table.
      Parameters:
      `conn` - connection

      `tableName` - name of the table to drop

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../NFEIOException.md)

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JdbcDataSource.md)
- [Next Class](NFEAbstractDataSource.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
