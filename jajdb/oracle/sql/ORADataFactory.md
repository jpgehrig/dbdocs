Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ORADataFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ORAData.md)
- [Next Class](RAW.md)

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

## Interface ORADataFactory

- All Superinterfaces:
  oracle.jdbc.internal.ObjectDataFactory

  ------------------------------------------------------------------------



      public interface ORADataFactory
      extends oracle.jdbc.internal.ObjectDataFactory

  ORAData factory interface.
  This interface complements ORAData. It is passed to getORAData() to create customized ORAData objects. The following example shows the typical use of this interface:

        EmpFactory factory = new EmpFactory();
        OracleResultSet rs = ... ;
        Emp m = (Emp) rs.getORAData(column, factory);
        ...


  This interface is the replacement of the old CustomDatumFactory interface that has been deprecated in the Oracle 9i release.

  Since:
  9iBeta

  See Also:
  `oracle.jdbc.ORAData`, `oracle.jdbc.PreparedStatement`, [`SQLData`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLData.html?is-external=true)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                        |
    |-------------------------|-----------------------------------------------------------------------------------------------|
    | [`ORAData`](ORAData.md) | `create``(`[`Datum`](Datum.md)` d, int sqlType)`<br>Create an ORAData from a oracle.sql.Datum |

<!-- -->

- - ### Method Detail

    - #### create

          ORAData create(Datum d,
                         int sqlType)
                  throws SQLException

      Create an ORAData from a oracle.sql.Datum
      This method creates the customized ORAData from a Datum. Sometimes, it is convenient to have the same class implement both ORAData and ORADataFactory.

      Parameters:
      `d` - The Datum to be used to initialize the Object being created.

      `sqlType` - The SQL type of the specified Datum.

      Returns:
      an Object that embeds information from d.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurred.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ORADataFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ORAData.md)
- [Next Class](RAW.md)

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
