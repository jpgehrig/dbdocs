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

- [Prev Class](OraNumberFormat.md)
- [Next Class](OraUnicodeProperty.md)

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

oracle.i18n.text

## Class OraSimpleDateFormat

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.text.Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

  - - [oracle.i18n.text.OraDateFormat](OraDateFormat.md)

    - - oracle.i18n.text.OraSimpleDateFormat

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OraSimpleDateFormat
      extends OraDateFormat

  The `OraSimpleDateFormat` class is a concrete class to do locale-sensitive formatting and parsing between date/time and string. It supports Oracle date/time formatting behavior.
  See Also:
  [`OraDateFormat`](OraDateFormat.md), [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`Format.Field`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.Field.html?is-external=true)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.i18n.text.[OraDateFormat](OraDateFormat.md)

      [`ALL_FIELD`](OraDateFormat.md)`, `[`AM_PM_FIELD`](OraDateFormat.md)`, `[`calendar`](OraDateFormat.md)`, `[`CENTRY_FIELD`](OraDateFormat.md)`, `[`DATE_FIELD`](OraDateFormat.md)`, `[`DAY_OF_WEEK_FIELD`](OraDateFormat.md)`, `[`DAY_OF_YEAR_FIELD`](OraDateFormat.md)`, `[`DEFAULT`](OraDateFormat.md)`, `[`ERA_FIELD`](OraDateFormat.md)`, `[`HOUR_FIELD`](OraDateFormat.md)`, `[`HOUR_OF_DAY_FIELD`](OraDateFormat.md)`, `[`ISO_WEEK_OF_YEAR_FIELD`](OraDateFormat.md)`, `[`ISO_YEAR_FIELD`](OraDateFormat.md)`, `[`JULIAN_DAY_FIELD`](OraDateFormat.md)`, `[`LONG`](OraDateFormat.md)`, `[`MILLISECOND_FIELD`](OraDateFormat.md)`, `[`MINUTE_FIELD`](OraDateFormat.md)`, `[`MONTH_FIELD`](OraDateFormat.md)`, `[`QUARTER_OF_YEAR_FIELD`](OraDateFormat.md)`, `[`SECOND_FIELD`](OraDateFormat.md)`, `[`SECONDS_FIELD`](OraDateFormat.md)`, `[`SHORT`](OraDateFormat.md)`, `[`TEXT_FIELD`](OraDateFormat.md)`, `[`TIMEZONE_FIELD`](OraDateFormat.md)`, `[`WEEK_OF_MONTH_FIELD`](OraDateFormat.md)`, `[`WEEK_OF_YEAR_FIELD`](OraDateFormat.md)`, `[`YEAR_FIELD`](OraDateFormat.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OraSimpleDateFormat``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, Locale)`                                                                                                                                                                                                                                                                                  |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, Locale)`                                                                                                                                                                             |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Constructs an `OraSimpleDateFormat` object that uses the given format pattern for the given locale.                                                                                                     |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`OraDateFormatSymbols`](OraDateFormatSymbols.md)` symbols)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, OraDateFormatSymbols, Locale)`                                                                                          |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`OraDateFormatSymbols`](OraDateFormatSymbols.md)` symbols, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Constructs an `OraSimpleDateFormat` object that uses the given format pattern and the given Oracle date/time symbols for the given locale. |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`OraDateFormatSymbols`](OraDateFormatSymbols.md)` symbols, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Constructs an `OraSimpleDateFormat` object that uses the given format pattern and the given Oracle date/time symbols for the given `OraLocaleInfo` object.                             |
    | `OraSimpleDateFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Constructs an `OraSimpleDateFormat` object that uses the given format pattern for the given `OraLocaleInfo` object.                                                                                                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                |
    |---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                  | `applyPattern``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>Applies the given format pattern of this date/time formatter.                                                                                                                                                                                                              |
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)             | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                                                               | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` object)`<br>Overrides the `equals` method.                                                                                                                                                                                                                                                    |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` date, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` pos)`<br>Formats a `Date` object into a date/time string. |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)             | `getLocale``()`<br>Returns the locale associated with this date/time formatter.                                                                                                                                                                                                                                                                                                                       |
    | [`OraDateFormatSymbols`](OraDateFormatSymbols.md)                                                       | `getOraDateFormatSymbols``()`<br>Returns the Oracle date/time format symbols or translations used in this formatter.                                                                                                                                                                                                                                                                                  |
    | `int`                                                                                                   | `hashCode``()`<br>Overrides the `hashCode` method.                                                                                                                                                                                                                                                                                                                                                    |
    | [`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)                 | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` pos)`<br>Parses a date/time string into a `Date` object, starting from the given parse position.                                                                             |
    | `void`                                                                                                  | `setOraDateFormatSymbols``(`[`OraDateFormatSymbols`](OraDateFormatSymbols.md)` sym)`<br>Sets the Oracle date/time format symbols or translations to the given `OraDateFormatSymbols` object for this formatter.                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)             | `toPattern``()`<br>Returns the format pattern associated with this date/time formatter.                                                                                                                                                                                                                                                                                                               |

    - ### Methods inherited from class oracle.i18n.text.[OraDateFormat](OraDateFormat.md)

      [`format`](OraDateFormat.md)`, `[`format`](OraDateFormat.md)`, `[`getCalendar`](OraDateFormat.md)`, `[`getDateInstance`](OraDateFormat.md)`, `[`getDateInstance`](OraDateFormat.md)`, `[`getDateInstance`](OraDateFormat.md)`, `[`getDateInstance`](OraDateFormat.md)`, `[`getDateTimeInstance`](OraDateFormat.md)`, `[`getDateTimeInstance`](OraDateFormat.md)`, `[`getDateTimeInstance`](OraDateFormat.md)`, `[`getDateTimeInstance`](OraDateFormat.md)`, `[`getDefaultDateFormatPattern`](OraDateFormat.md)`, `[`getDefaultDateFormatPattern`](OraDateFormat.md)`, `[`getDefaultDateTimeFormatPattern`](OraDateFormat.md)`, `[`getDefaultDateTimeFormatPattern`](OraDateFormat.md)`, `[`getDefaultTimeFormatPattern`](OraDateFormat.md)`, `[`getDefaultTimeFormatPattern`](OraDateFormat.md)`, `[`getInstance`](OraDateFormat.md)`, `[`getTimeInstance`](OraDateFormat.md)`, `[`getTimeInstance`](OraDateFormat.md)`, `[`getTimeInstance`](OraDateFormat.md)`, `[`getTimeZone`](OraDateFormat.md)`, `[`parse`](OraDateFormat.md)`, `[`parseObject`](OraDateFormat.md)`, `[`setCalendar`](OraDateFormat.md)`, `[`setTimeZone`](OraDateFormat.md)

    <!-- -->

    - ### Methods inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-)`, `[`formatToCharacterIterator`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#formatToCharacterIterator-java.lang.Object-)`, `[`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, Locale)`
      Constructs an `OraSimpleDateFormat` object that uses the default date/time formatting sytle for the default locale.

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern)
                              throws ParseException

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, Locale)`
      Constructs an `OraSimpleDateFormat` object that uses the given format pattern for the default locale.
      Parameters:
      `pattern` - the given format pattern

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern,
                                     Locale locale)
                              throws ParseException

      Constructs an `OraSimpleDateFormat` object that uses the given format pattern for the given locale.
      Parameters:
      `pattern` - the given format pattern

      `locale` - the given locale

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern,
                                     OraLocaleInfo localeInfo)
                              throws ParseException

      Constructs an `OraSimpleDateFormat` object that uses the given format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `pattern` - the given format pattern

      `localeInfo` - the given `OraLocaleInfo` object

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern,
                                     OraDateFormatSymbols symbols)
                              throws ParseException

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraSimpleDateFormat.OraSimpleDateFormat(String, OraDateFormatSymbols, Locale)`
      Constructs an `OraSimpleDateFormat` object that uses the given format pattern and the given Oracle date/time symbols for the default locale.
      Parameters:
      `pattern` - the given format pattern

      `symbols` - the given Oracle date/time symbols

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern,
                                     OraDateFormatSymbols symbols,
                                     Locale locale)
                              throws ParseException

      Constructs an `OraSimpleDateFormat` object that uses the given format pattern and the given Oracle date/time symbols for the given locale.
      Parameters:
      `pattern` - the given format pattern

      `symbols` - the given Oracle date/time symbols

      `locale` - the given locale

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### OraSimpleDateFormat

          public OraSimpleDateFormat(String pattern,
                                     OraDateFormatSymbols symbols,
                                     OraLocaleInfo localeInfo)
                              throws ParseException

      Constructs an `OraSimpleDateFormat` object that uses the given format pattern and the given Oracle date/time symbols for the given `OraLocaleInfo` object.
      Parameters:
      `pattern` - the given format pattern

      `symbols` - the given Oracle date/time symbols

      `localeInfo` - the given `OraLocaleInfo` object

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

  <!-- -->

  - ### Method Detail

    - #### applyPattern

          public void applyPattern(String pattern)
                            throws ParseException

      Applies the given format pattern of this date/time formatter.
      Parameters:
      `pattern` - the given format pattern

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern is invalid

    <!-- -->

    - #### format

          public StringBuffer format(Date date,
                                     StringBuffer toAppendTo,
                                     FieldPosition pos)

      Formats a `Date` object into a date/time string. Sets field position if needed.
      Specified by:
      [`format`](OraDateFormat.md) in class [`OraDateFormat`](OraDateFormat.md)

      Parameters:
      `date` - the date/time object to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted date/time string.

      `pos` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with the formatted date/time string

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if any error occurs in the format operation

    <!-- -->

    - #### getOraDateFormatSymbols

          public OraDateFormatSymbols getOraDateFormatSymbols()

      Returns the Oracle date/time format symbols or translations used in this formatter. The symbols include: month names, abbreviated month names, names of day-of-the-week, abbreviated names of day-of-the-week, era strings, and meridian indicators.
      Returns:
      an `OracleDateFormatSymbols` object

      See Also:
      [`OraDateFormatSymbols`](OraDateFormatSymbols.md)

    <!-- -->

    - #### setOraDateFormatSymbols

          public void setOraDateFormatSymbols(OraDateFormatSymbols sym)

      Sets the Oracle date/time format symbols or translations to the given `OraDateFormatSymbols` object for this formatter.
      Parameters:
      `sym` - the given `OraDateFormatSymbols` object

    <!-- -->

    - #### parse

          public Date parse(String text,
                            ParsePosition pos)

      Parses a date/time string into a `Date` object, starting from the given parse position.
      Specified by:
      [`parse`](OraDateFormat.md) in class [`OraDateFormat`](OraDateFormat.md)

      Parameters:
      `text` - the date/time string

      `pos` - indicates where to start the parsing on input. On output, returns where the parse ends if parsing succeeds, or the start index if it fails.

      Returns:
      a `Date` object

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if the format pattern associated with this formatter is not valid for parsing or the given date/time string cannot be parsed into a `Date` object

    <!-- -->

    - #### toPattern

          public String toPattern()

      Returns the format pattern associated with this date/time formatter.
      Returns:
      a format pattern string

    <!-- -->

    - #### getLocale

          public Locale getLocale()

      Returns the locale associated with this date/time formatter.
      Returns:
      a Java `Locale` object

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](OraDateFormat.md) in class [`OraDateFormat`](OraDateFormat.md)

      Returns:
      a cloned object

    <!-- -->

    - #### equals

          public boolean equals(Object object)

      Overrides the `equals` method.
      Overrides:
      [`equals`](OraDateFormat.md) in class [`OraDateFormat`](OraDateFormat.md)

      Parameters:
      `object` - an object to be compared

      Returns:
      `true` if two objects are identical, otherwise `false`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides the `hashCode` method.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a hash value

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

- [Prev Class](OraNumberFormat.md)
- [Next Class](OraUnicodeProperty.md)

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
