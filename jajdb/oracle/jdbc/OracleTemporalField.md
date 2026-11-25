Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTemporalField.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleStruct.md)
- [Next Class](OracleTranslatingConnection.md)

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

## Class OracleTemporalField

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.OracleTemporalField

<!-- -->

-

  ------------------------------------------------------------------------



      public final class OracleTemporalField
      extends Object

  TemporalFields specific to Oracle Database.
  This class defines TemporalFields that are specific to Oracle Database.

  ### Signed year of era

  This field represents the year as a non-zero integer where 1 BCE is is represented as -1. This is the representation used by the Oracle Database. This field is useful for parsing and formatting dates for use with Oracle Database.
  The field ChronoField.YEAR represents the year as an integer where the value 0 represents 1 BCE and -1 represents 2 BCE. ChronoField.YEAR_OF_ERA represents the positive value of the year within the era. The YEAR_OF_ERA value of 1 BCE is 1. Neither corresponds to the Oracle Database representation.

  Example

       DateTimeFormatter f = new DateTimeFormatterBuilder()
           .appendValue(OracleField.SIGNED_YEAR_OF_ERA)
           .appendLiteral("-")
           .appendValue(ChronoField.MONTH_OF_YEAR)
           .appendLiteral("-")
           .appendValue(ChronoField.DAY_OF_MONTH)
           .toFormatter();
         LocalDate d = f.parse(rs.getObject(i, String.class), TemporalQueries.localDate());
         ps.setObject(j, f.format(d), JDBCType.VARCHAR);

  Since:
  12.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                         | Field and Description                                                                                    |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------|
    | `static java.time.temporal.TemporalField` | `SIGNED_YEAR_OF_ERA`<br>The field that represents the signed year of the era as used by Oracle Database. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Field Detail

    - #### SIGNED_YEAR_OF_ERA

          public static final java.time.temporal.TemporalField SIGNED_YEAR_OF_ERA

      The field that represents the signed year of the era as used by Oracle Database.
      This field allows the signed year of era value to be queried and set. The signed year of era has values from Long.MAX_VALUE to Long.MIN_VALUE excluding 0.

      The signed year of era can only be calculated if the year is available.

      This field is an immutable and thread-safe singleton.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTemporalField.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleStruct.md)
- [Next Class](OracleTranslatingConnection.md)

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
