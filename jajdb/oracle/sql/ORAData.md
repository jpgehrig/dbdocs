Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ORAData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OpaqueDescriptor.md)
- [Next Class](ORADataFactory.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.sql

## Interface ORAData

- All Superinterfaces:
  oracle.jdbc.internal.ObjectData

  <!-- -->

  All Known Implementing Classes:
  [ANYDATA](ANYDATA.md), [ArrayDescriptor](ArrayDescriptor.md), [OpaqueDescriptor](OpaqueDescriptor.md), [StructDescriptor](StructDescriptor.md), [TypeDescriptor](TypeDescriptor.md)

  ------------------------------------------------------------------------



      public interface ORAData
      extends oracle.jdbc.internal.ObjectData

  Oracle interface for customized user-defined types.
  This is an interface for encapsulating SQL types into Java types of the user's choice. User's class, which implements the ORAData interface, can present a customized version of the SQL type.

  One can have lots of different classes implementing CustomDatum for a particular SQL type but generally each type implementing ORAData will be used for only a single SQL type.

  For use as a SQL type, a class that implements ORAData must contain the following static fields and methods:

        public static ORADataFactory getFactory() { ... }

        public static final int _SQL_TYPECODE = oracle.jdbc.OracleTypes....;

        // for STRUCT and ARRAY
        public static final String _SQL_name="O___";

        // for REF and ARRAY
        public static final String _SQL_BASETYPE = "...";


  This interface is the replacement of the old CustomDatum interface that has been deprecated in the Oracle 9i release.

  Since:
  9iBeta

  See Also:
  `oracle.jdbc.ORADataFactory`, `oracle.jdbc.PreparedStatement`, [`SQLData`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLData.html?is-external=true)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                                                                                         |
    |---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Datum`](Datum.md) | `toDatum``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` c)`<br>Extract an oracle.sql.Datum object. |

<!-- -->

- - ### Method Detail

    - #### toDatum

          Datum toDatum(Connection c)
                 throws SQLException

      Extract an oracle.sql.Datum object.
      This method is invoked by setORAData() to extract a Datum. The implementation of this method must return the correct type of Datum.

      Although most implementation will ignore the connection, it is occassionally needed. For example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a Datum contaning the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ORAData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OpaqueDescriptor.md)
- [Next Class](ORADataFactory.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
