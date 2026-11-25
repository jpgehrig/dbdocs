Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](OraResourceBundle.md)
- Next Class

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

oracle.i18n.util

## Class OraSQLUtil

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.OraSQLUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraSQLUtil
      extends Object

  The `OraSQLUtil` class is an Oracle SQL utility class.
  The following functionality is available in this class:

  - Data Validation - validates whether data can be stored safely into the database in the specified character set.
  - Data Conversion - converts all characters that cannot be stored in the database in the specified charcter set into Unicode escape forms, such as `\[0-9A-Z]{4}`, for the `UNISTR` function
  - Database session synchronization - synchronizes the NLS database session parameters with the Java locale or the Oracle language and territory

  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `escapeUNISTR``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dbCharset)`<br>Escapes the string into `UNISTR` form if the character is not supported by the database character set.                                                                                                                   |
    | `static boolean`                                                                                     | `isValidIdentifier``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` srcstr, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` dbCharset)`<br>Checks if the string is valid in the database character set.                                                                                                                                                     |
    | `static boolean`                                                                                     | `synchronizeLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale, `[`Connection`](http://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` con)`<br>Synchronizes the session NLS parameters with the locale.                                                                                                                                                        |
    | `static boolean`                                                                                     | `synchronizeLocale``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oralanguage, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraterritory, `[`Connection`](http://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` con)`<br>Synchronizes the database session NLS parameters with the Oracle language and territory names. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### isValidIdentifier

          public static boolean isValidIdentifier(String srcstr,
                                                  String dbCharset)
                                           throws UnsupportedEncodingException

      Checks if the string is valid in the database character set.
      Parameters:
      `srcstr` - a string to be examined

      `dbCharset` - Oracle database character set name

      Returns:
      `true` if the data is valid in the database character set, otherwise `false`

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the `dbCharset` parameter is invalid

    <!-- -->

    - #### escapeUNISTR

          public static String escapeUNISTR(String str,
                                            String dbCharset)
                                     throws UnsupportedEncodingException

      Escapes the string into `UNISTR` form if the character is not supported by the database character set.
      Parameters:
      `str` - a string to be examined

      `dbCharset` - Oracle database character set name

      Returns:
      a `UNISTR` string containing Unicode escaped form if the character is not supported by the character set

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if the `dbCharset` parameter is invalid

    <!-- -->

    - #### synchronizeLocale

          public static boolean synchronizeLocale(Locale locale,
                                                  Connection con)
                                           throws SQLException

      Synchronizes the session NLS parameters with the locale.
      This executes `ALTER SESSION` SQL commands to set NLS session parameters to synchronize the locale and attributes in this object. The following session parameters are updated:

      - NLS_LANGUAGE
      - NLS_TERRITORY

      Parameters:
      `locale` - Java locale object

      `con` - database connection

      Returns:
      `true` if successful, otherwise `false`

      Throws:
      [`SQLException`](http://docs.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a SQL exception occurs

    <!-- -->

    - #### synchronizeLocale

          public static boolean synchronizeLocale(String oralanguage,
                                                  String oraterritory,
                                                  Connection con)
                                           throws SQLException

      Synchronizes the database session NLS parameters with the Oracle language and territory names.
      This executes `ALTER SESSION` SQL commands to set NLS session parameters to synchronize the locale and attributes in this object. The following session parameters are updated:

      - NLS_LANGUAGE
      - NLS_TERRITORY

      Parameters:
      `oralanguage` - Oracle language name

      `oraterritory` - Oracle territory name

      `con` - database connection

      Returns:
      `true` if successful, otherwise `false`

      Throws:
      [`SQLException`](http://docs.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a SQL exception occurs

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](OraResourceBundle.md)
- Next Class

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

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
