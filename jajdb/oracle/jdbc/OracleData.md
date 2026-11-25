Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionWrapper.CloseInvocationHandler.md)
- [Next Class](OracleDatabaseException.md)

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

oracle.jdbc

## Interface OracleData

- All Known Implementing Classes:
  [ANYDATA](../sql/ANYDATA.md), [ArrayDescriptor](../sql/ArrayDescriptor.md), [OpaqueDescriptor](../sql/OpaqueDescriptor.md), [StructDescriptor](../sql/StructDescriptor.md), [TypeDescriptor](../sql/TypeDescriptor.md)

  ------------------------------------------------------------------------



      public interface OracleData

  Oracle interface for customize user-defined types.
  This is a new interface for encapsualting SQL types into Java types of the user's choice replacing ORAData. Users should use OracleData instead of ORAData. A User's class, which implements the OracleData interface, can present a customized version of the SQL type. A class XXXClass implementing OracleData must also implement the following method :

        public static XXXClass valueOf( YYYType value) throws SQLException


  where YYYtype can be one of the specific Java Object types in column 2 of Table B-3 of the JDBC spec.

  This interface is the replacement of the ORAData interface

  Since:
  11.2.0.3

  See Also:
  [`OracleDataFactory`](OracleDataFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `toJDBCObject``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Extract a jdbc Object. |

<!-- -->

- - ### Method Detail

    - #### toJDBCObject

          Object toJDBCObject(Connection conn)
                       throws SQLException

      Extract a jdbc Object.
      This method is invoked by setObject() to extract the jdbc Object. The implementation must return the jdbc Object that correctly represents the underlying SQLType.

      Although most implementation will ignore the connection, it is ocassionally needed. for example, if the class embeds CHAR attributes, connection may be needed to determine the database character set.

      Parameters:
      `conn` - The connection into which the value is being sent.

      Returns:
      a jdbc Object contianing the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionWrapper.CloseInvocationHandler.md)
- [Next Class](OracleDatabaseException.md)

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
