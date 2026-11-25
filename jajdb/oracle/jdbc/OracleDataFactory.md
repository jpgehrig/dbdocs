Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDatabaseMetaData.DataTypeSource.md)
- [Next Class](OracleDriver.md)

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

## Interface OracleDataFactory

-

  ------------------------------------------------------------------------



      public interface OracleDataFactory

  OracleData factory interface.
  This interface complements OracleData. It is passed to getObject() to create customized OracleData objects. The following example shows the typical use of this interface:

        EmpFactory factory = new EmpFactory();
        OracleResultSet rs = ... ;
        Emp m = (Emp) rs.getObject(column, factory);
        ...


  This interface is the replacement of the ORADataFactory

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                                          |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleData`](OracleData.md) | `create``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` jdbcValue, int sqlType)`<br>Create an OracleData from a jdbc Object |

<!-- -->

- - ### Method Detail

    - #### create

          OracleData create(Object jdbcValue,
                            int sqlType)
                     throws SQLException

      Create an OracleData from a jdbc Object
      This method creates the customized OracleData from a jdbc Object. Sometimes, it is convenient to have the same class implement both OracleData and OracleDataFactory.

      Parameters:
      `jdbcValue` - The jdbc Object to be used to initialize the Object being created.

      `sqlType` - The SQL type of the specified Datum.

      Returns:
      an Object that embeds information from jdbcValue.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleDataFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleDatabaseMetaData.DataTypeSource.md)
- [Next Class](OracleDriver.md)

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
