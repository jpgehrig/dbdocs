Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CustomDatum.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ConverterArchive.md)
- [Next Class](CustomDatumFactory.md)

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

## Interface CustomDatum

- All Superinterfaces:
  oracle.jdbc.internal.ObjectData

  ------------------------------------------------------------------------



      public interface CustomDatum
      extends oracle.jdbc.internal.ObjectData

  This is an interface for encapsulating SQL Types into Java types of the user's choice. The user class can present a customized version of the SQL type. You can get and set values of the Java type as appropriate.

  You can have lots of different classes implementing CustomDatum for a particular SQLType but generally each type implementing CustomDatum will be used for only a single SQLType.

  The original motivation for this class is the jpub generator which examines SQL types (especially Object types) and creates "well typed" java versions. This includes Object types, Ref types and Array types.

  It was also partially "inspired" by the jdbc2 SQLData interface.
  For use as a SQLJ type a class that implements CustomDatum will contain static fields and methods declared as

        public static CustomDatumFactory getFactory() ...

        public static final int _SQLJ_TYPECODE = oracle.jdbc.driver.Types ....;

        // for STRUCT and ARRAY
        public static final String _SQLJ_name="O____" ;

        // for REF and ARRAY
        public static final String _SQLJ_BASETYPE = "...." ;


  Typical use would be

        Emp e = ...
        OraclePreparedStatement stmt = .... ;
        stmt.setCustom(n, e);


  See Also:
  [`CustomDatumFactory`](CustomDatumFactory.md), `oracle.jdbc.driver.PreparedStatement`, [`SQLData`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLData.html?is-external=true)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                              |
    |---------------------|-----------------------------------------------------------------------------------------------------|
    | [`Datum`](Datum.md) | `toDatum``(oracle.jdbc.driver.OracleConnection c)`<br>Called by setOracleObject to extract a Datum. |

<!-- -->

- - ### Method Detail

    - #### toDatum

          Datum toDatum(oracle.jdbc.driver.OracleConnection c)
                 throws SQLException

      Called by setOracleObject to extract a Datum. It is the CustomDatum's responsibility to be sure that it returns the correct category of Datum.
      Most EmbedDatum's will ignore the connection, but it is occassionally needed. For example, if the class embeds CHAR's it may nees the connection to determine the database character set.

      Parameters:
      `c` - The connection into which the value is being sent.

      Returns:
      a Datum containg the value to be sent into the connection.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CustomDatum.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](ConverterArchive.md)
- [Next Class](CustomDatumFactory.md)

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
