Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CustomDatumFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CustomDatum.md)
- [Next Class](DATE.md)

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

## Interface CustomDatumFactory

- All Superinterfaces:
  oracle.jdbc.internal.ObjectDataFactory

  ------------------------------------------------------------------------



      public interface CustomDatumFactory
      extends oracle.jdbc.internal.ObjectDataFactory

  This interface complements CustomDatum. It is passed to getCustom methods to create specific kinds of objects.
  Typical use is

        EmpFactory factory = new EmpFactory();
        OracleResultSet rs = ... ;
        Emp m = (Emp)rs.getCustom(n, factory);
        ...


<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                            |
    |---------------------------------|---------------------------------------------------------------------------------------------------|
    | [`CustomDatum`](CustomDatum.md) | `create``(`[`Datum`](Datum.md)` d, int sqlType)`<br>create an Object from SQL Type and return it. |

<!-- -->

- - ### Method Detail

    - #### create

          CustomDatum create(Datum d,
                             int sqlType)
                      throws SQLException

      create an Object from SQL Type and return it. It is sometimes convenient to have the same class implement both CustomDatum and CustomDatumFactory, but normally they are distinct.
      Parameters:
      `d` - some SQL data that should be used to initialize an Object.

      `sqlType` - the SQL type that the

      Returns:
      an Object that embeds information from d.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CustomDatumFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CustomDatum.md)
- [Next Class](DATE.md)

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
