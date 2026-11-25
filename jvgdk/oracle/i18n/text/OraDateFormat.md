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

- [Prev Class](OraCollator.md)
- [Next Class](OraDateFormatSymbols.md)

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

## Class OraDateFormat

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.text.Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

  - - oracle.i18n.text.OraDateFormat

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [OraSimpleDateFormat](OraSimpleDateFormat.md)

  ------------------------------------------------------------------------



      public abstract class OraDateFormat
      extends Format

  The `OraDateFormat` class is an abstract class to do locale-sensitive formatting and parsing between date/time and string. It supports Oracle date/time formatting behavior.
  See Also:
  `OraSimpleDateFormat`, [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`Format.Field`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.Field.html?is-external=true)

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                           | Field and Description                                                                                     |
    |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
    | `static int`                                                                                                | `ALL_FIELD`<br>Constant for `ALL_FIELD` alignment.                                                        |
    | `static int`                                                                                                | `AM_PM_FIELD`<br>Constant for `AM_PM_FIELD` alignment.                                                    |
    | `protected `[`Calendar`](http://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true) | `calendar`<br>The calendar that this `OraDateFormat` object uses to calculate the date/time field values. |
    | `static int`                                                                                                | `CENTRY_FIELD`<br>Constant for `CENTRY_FIELD` alignment.                                                  |
    | `static int`                                                                                                | `DATE_FIELD`<br>Constant for `DATE_FIELD` alignment.                                                      |
    | `static int`                                                                                                | `DAY_OF_WEEK_FIELD`<br>Constant for `DAY_OF_WEEK_FIELD` alignment.                                        |
    | `static int`                                                                                                | `DAY_OF_YEAR_FIELD`<br>Constant for `DAY_OF_YEAR_FIELD` alignment.                                        |
    | `static int`                                                                                                | `DEFAULT`<br>Constant for `DEFAULT` format style.                                                         |
    | `static int`                                                                                                | `ERA_FIELD`<br>Constant for `ERA_FIELD` alignment.                                                        |
    | `static int`                                                                                                | `HOUR_FIELD`<br>Constant for `HOUR_FIELD` alignment.                                                      |
    | `static int`                                                                                                | `HOUR_OF_DAY_FIELD`<br>Constant for `HOUR_OF_DAY_FIELD` alignment.                                        |
    | `static int`                                                                                                | `ISO_WEEK_OF_YEAR_FIELD`<br>Constant for `ISO_WEEK_OF_YEAR_FIELD` alignment.                              |
    | `static int`                                                                                                | `ISO_YEAR_FIELD`<br>Constant for `ISO_YEAR_FIELD` alignment.                                              |
    | `static int`                                                                                                | `JULIAN_DAY_FIELD`<br>Constant for `JULIAN_DAY_FIELD` alignment.                                          |
    | `static int`                                                                                                | `LONG`<br>Constant for date `LONG` format style.                                                          |
    | `static int`                                                                                                | `MILLISECOND_FIELD`<br>Constant for `MILLISECOND_FIELD` alignment.                                        |
    | `static int`                                                                                                | `MINUTE_FIELD`<br>Constant for `MINUTE_FIELD` alignment.                                                  |
    | `static int`                                                                                                | `MONTH_FIELD`<br>Constant for `MONTH_FIELD` alignment.                                                    |
    | `static int`                                                                                                | `QUARTER_OF_YEAR_FIELD`<br>Constant for `QUARTER_OF_YEAR_FIELD` alignment.                                |
    | `static int`                                                                                                | `SECOND_FIELD`<br>Constant for `SECOND_FIELD` alignment.                                                  |
    | `static int`                                                                                                | `SECONDS_FIELD`<br>Constant for `SECONDS_FIELD` alignment.                                                |
    | `static int`                                                                                                | `SHORT`<br>Constant for date/time `SHORT` format style.                                                   |
    | `static int`                                                                                                | `TEXT_FIELD`<br>Constant for `TEXT_FIELD` alignment.                                                      |
    | `static int`                                                                                                | `TIMEZONE_FIELD`<br>Constant for `TIMEZONE_FIELD` alignment.                                              |
    | `static int`                                                                                                | `WEEK_OF_MONTH_FIELD`<br>Constant for `WEEK_OF_MONTH_FIELD` alignment.                                    |
    | `static int`                                                                                                | `WEEK_OF_YEAR_FIELD`<br>Constant for `WEEK_OF_YEAR_FIELD` alignment.                                      |
    | `static int`                                                                                                | `YEAR_FIELD`<br>Constant for `YEAR_FIELD` alignment.                                                      |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OraDateFormat``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                        | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                                                                                                                                                                                                                    |
    | `boolean`                                                                                                          | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Overrides the `equals` method.                                                                                                                                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                        | `format``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` date)`<br>Formats a `Date` object into a date/time string.                                                                                                                                                                                                                                                  |
    | `abstract `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` date, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats a `Date` object into a date/time string. |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)            | `format``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats an object into a date/time string.    |
    | [`Calendar`](http://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)                    | `getCalendar``()`<br>Returns the calendar associated with this date/time formatter.                                                                                                                                                                                                                                                                                                                             |
    | `static OraDateFormat`                                                                                             | `getDateInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateInstance(int, Locale)`                                                                                                                                                                                                                                                                   |
    | `static OraDateFormat`                                                                                             | `getDateInstance``(int style)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateInstance(int, Locale)`                                                                                                                                                                                                                                                          |
    | `static OraDateFormat`                                                                                             | `getDateInstance``(int style, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a date formatter that uses the given date formatting style for the given locale.                                                                                                                                                                                |
    | `static OraDateFormat`                                                                                             | `getDateInstance``(int style, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a date formatter that uses the given date formatting style for the given `OraLocaleInfo` object.                                                                                                                                                                                                            |
    | `static OraDateFormat`                                                                                             | `getDateTimeInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`                                                                                                                                                                                                                                                           |
    | `static OraDateFormat`                                                                                             | `getDateTimeInstance``(int dateStyle)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`                                                                                                                                                                                                                                              |
    | `static OraDateFormat`                                                                                             | `getDateTimeInstance``(int dateStyle, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a date/time formatter that uses the given date formatting style and the default time formatting style for the given locale.                                                                                                                             |
    | `static OraDateFormat`                                                                                             | `getDateTimeInstance``(int dateStyle, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a date/time formatter that uses the given date formatting style and the default time formatting style for the given `OraLocaleInfo` object.                                                                                                                                                         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultDateFormatPattern``(int style, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default date format pattern for the given date formatting style and the given locale.                                                                                                                                                           |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultDateFormatPattern``(int style, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns the default date format pattern for the given date formatting style and the given `OraLocaleInfo` object.                                                                                                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultDateTimeFormatPattern``(int dateStyle, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default date/time format pattern for the given date formatting style and the given locale.                                                                                                                                              |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultDateTimeFormatPattern``(int dateStyle, `[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns the default date/time format pattern for the given date formatting style and the given `OraLocaleInfo` object.                                                                                                                                                                          |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultTimeFormatPattern``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default time format pattern for the given locale.                                                                                                                                                                                                          |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultTimeFormatPattern``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns the default time format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                                      |
    | `static OraDateFormat`                                                                                             | `getInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`                                                                                                                                                                                                                                                                   |
    | `static OraDateFormat`                                                                                             | `getTimeInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getTimeInstance(Locale)`                                                                                                                                                                                                                                                                        |
    | `static OraDateFormat`                                                                                             | `getTimeInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a time formatter for the given locale.                                                                                                                                                                                                                                     |
    | `static OraDateFormat`                                                                                             | `getTimeInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a time formatter for the given `OraLocaleInfo` object.                                                                                                                                                                                                                                                                 |
    | [`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)                    | `getTimeZone``()`<br>Returns the time zone associated with the calendar of this formatter.                                                                                                                                                                                                                                                                                                                      |
    | [`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)                            | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text)`<br>Parses a date/time string into a date.                                                                                                                                                                                                                                                         |
    | `abstract `[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)                 | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` pos)`<br>Parses a date/time string into a date, starting from the given parse position.                                                                                                |
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                        | `parseObject``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` pos)`<br>Parses a date/time string into a (`Date`) object, starting from the given parse position.                                                                               |
    | `void`                                                                                                             | `setCalendar``(`[`Calendar`](http://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` calendar)`<br>Sets the given calendar to be used by this date/time formatter.                                                                                                                                                                                                                  |
    | `void`                                                                                                             | `setTimeZone``(`[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` timezone)`<br>Sets the given time zone to be used by the calendar of this formatter.                                                                                                                                                                                                           |

    - ### Methods inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-)`, `[`formatToCharacterIterator`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#formatToCharacterIterator-java.lang.Object-)`, `[`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### ERA_FIELD

          public static final int ERA_FIELD

      Constant for `ERA_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### YEAR_FIELD

          public static final int YEAR_FIELD

      Constant for `YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MONTH_FIELD

          public static final int MONTH_FIELD

      Constant for `MONTH_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATE_FIELD

          public static final int DATE_FIELD

      Constant for `DATE_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### HOUR_OF_DAY_FIELD

          public static final int HOUR_OF_DAY_FIELD

      Constant for `HOUR_OF_DAY_FIELD` alignment. Used to specify the field position for formatting. The `HOUR_OF_DAY_FIELD` is used for zero-base, 24-hour clock (0 ~ 23).
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MINUTE_FIELD

          public static final int MINUTE_FIELD

      Constant for `MINUTE_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECOND_FIELD

          public static final int SECOND_FIELD

      Constant for `SECOND_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MILLISECOND_FIELD

          public static final int MILLISECOND_FIELD

      Constant for `MILLISECOND_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DAY_OF_WEEK_FIELD

          public static final int DAY_OF_WEEK_FIELD

      Constant for `DAY_OF_WEEK_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DAY_OF_YEAR_FIELD

          public static final int DAY_OF_YEAR_FIELD

      Constant for `DAY_OF_YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WEEK_OF_YEAR_FIELD

          public static final int WEEK_OF_YEAR_FIELD

      Constant for `WEEK_OF_YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WEEK_OF_MONTH_FIELD

          public static final int WEEK_OF_MONTH_FIELD

      Constant for `WEEK_OF_MONTH_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AM_PM_FIELD

          public static final int AM_PM_FIELD

      Constant for `AM_PM_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### HOUR_FIELD

          public static final int HOUR_FIELD

      Constant for `HOUR_FIELD` alignment. Used to specify the field position for formatting. The `HOUR_FIELD` is used for one-base, 12-hour clock (1 ~ 12).
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TIMEZONE_FIELD

          public static final int TIMEZONE_FIELD

      Constant for `TIMEZONE_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ALL_FIELD

          public static final int ALL_FIELD

      Constant for `ALL_FIELD` alignment. Used to specify the field position for formatting. The `ALL_FIELD` is used to indicate all fields specified in a format pattern.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CENTRY_FIELD

          public static final int CENTRY_FIELD

      Constant for `CENTRY_FIELD` alignment. Used to specify the field position for formatting. Centry is one greater than the first two digits of a four-digit year.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JULIAN_DAY_FIELD

          public static final int JULIAN_DAY_FIELD

      Constant for `JULIAN_DAY_FIELD` alignment. Used to specify the field position for formatting. The Julian day is number of days since January 1, 4712 BC.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### QUARTER_OF_YEAR_FIELD

          public static final int QUARTER_OF_YEAR_FIELD

      Constant for `QUARTER_OF_YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SECONDS_FIELD

          public static final int SECONDS_FIELD

      Constant for `SECONDS_FIELD` alignment. Used to specify the field position for formatting. The `SECONDS_FIELD` is for number of seconds past midnight.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEXT_FIELD

          public static final int TEXT_FIELD

      Constant for `TEXT_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ISO_YEAR_FIELD

          public static final int ISO_YEAR_FIELD

      Constant for `ISO_YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ISO_WEEK_OF_YEAR_FIELD

          public static final int ISO_WEEK_OF_YEAR_FIELD

      Constant for `ISO_WEEK_OF_YEAR_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SHORT

          public static final int SHORT

      Constant for date/time `SHORT` format style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LONG

          public static final int LONG

      Constant for date `LONG` format style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT

          public static final int DEFAULT

      Constant for `DEFAULT` format style. For date, it is equivalent to Oracle server default date format. For time, it is equivalent to the time `SHORT` format style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### calendar

          protected Calendar calendar

      The calendar that this `OraDateFormat` object uses to calculate the date/time field values. Subclasses should initialize the `calendar` object accordingly based on the locale associated with this `OraDateFormat` object.

  <!-- -->

  - ### Constructor Detail

    - #### OraDateFormat

          public OraDateFormat()

  <!-- -->

  - ### Method Detail

    - #### getDateInstance

          public static final OraDateFormat getDateInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateInstance(int, Locale)`
      Returns a date formatter that uses the default date formatting style for the default locale.
      Returns:
      a date formatter

    <!-- -->

    - #### getDateInstance

          public static final OraDateFormat getDateInstance(int style)

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateInstance(int, Locale)`
      Returns a date formatter that uses the given date formatting style for the default locale.
      Parameters:
      `style` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      Returns:
      a date formatter

    <!-- -->

    - #### getDateInstance

          public static final OraDateFormat getDateInstance(int style,
                                                            Locale locale)

      Returns a date formatter that uses the given date formatting style for the given locale.
      Parameters:
      `style` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      `locale` - the given locale

      Returns:
      a date formatter

    <!-- -->

    - #### getDateInstance

          public static final OraDateFormat getDateInstance(int style,
                                                            OraLocaleInfo localeInfo)

      Returns a date formatter that uses the given date formatting style for the given `OraLocaleInfo` object.
      Parameters:
      `style` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a date formatter

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if the given date formatting style is invalid

    <!-- -->

    - #### getDateTimeInstance

          public static final OraDateFormat getDateTimeInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`
      Returns a date/time formatter that uses the default date/time formatting style for the default locale.
      Returns:
      a date/time formatter

    <!-- -->

    - #### getDateTimeInstance

          public static final OraDateFormat getDateTimeInstance(int dateStyle)

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`
      Returns a date/time formatter that uses the given date formatting style and the default time formatting style for the default locale.
      Parameters:
      `dateStyle` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      Returns:
      a date/time formatter

    <!-- -->

    - #### getDateTimeInstance

          public static final OraDateFormat getDateTimeInstance(int dateStyle,
                                                                Locale locale)

      Returns a date/time formatter that uses the given date formatting style and the default time formatting style for the given locale.
      Parameters:
      `dateStyle` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      `locale` - the given locale

      Returns:
      a date/time formatter

    <!-- -->

    - #### getDateTimeInstance

          public static final OraDateFormat getDateTimeInstance(int dateStyle,
                                                                OraLocaleInfo localeInfo)

      Returns a date/time formatter that uses the given date formatting style and the default time formatting style for the given `OraLocaleInfo` object.
      Parameters:
      `dateStyle` - the given date formatting style; options are `SHORT`, `LONG` or `DEFAULT`

      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a date/time formatter

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if the given date formatting style is invalid

    <!-- -->

    - #### getInstance

          public static final OraDateFormat getInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getDateTimeInstance(int, Locale)`
      Returns a date/time formatter that uses the default date/time formatting style for the default locale.
      Returns:
      a date/time formatter

    <!-- -->

    - #### getTimeInstance

          public static final OraDateFormat getTimeInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormat.getTimeInstance(Locale)`
      Returns a time formatter that uses the default time formatting style for the default locale.
      Returns:
      a time formatter

    <!-- -->

    - #### getTimeInstance

          public static final OraDateFormat getTimeInstance(Locale locale)

      Returns a time formatter for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      a time formatter

    <!-- -->

    - #### getTimeInstance

          public static final OraDateFormat getTimeInstance(OraLocaleInfo localeInfo)

      Returns a time formatter for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a time formatter

    <!-- -->

    - #### format

          public final String format(Date date)

      Formats a `Date` object into a date/time string.
      Parameters:
      `date` - the date/time object to be formatted into a date/time string

      Returns:
      the formatted date/time string

    <!-- -->

    - #### format

          public abstract StringBuffer format(Date date,
                                              StringBuffer toAppendTo,
                                              FieldPosition fieldPosition)

      Formats a `Date` object into a date/time string. Sets field position if it is needed.
      Parameters:
      `date` - the date/time object to be formatted into a date/time string.

      `toAppendTo` - the string buffer to be appended with the formatted date/time string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with the formatted date/time string

    <!-- -->

    - #### format

          public final StringBuffer format(Object obj,
                                           StringBuffer toAppendTo,
                                           FieldPosition fieldPosition)

      Formats an object into a date/time string. Sets field position if it is needed.
      Specified by:
      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-java.lang.StringBuffer-java.text.FieldPosition-) in class [`Format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      Parameters:
      `obj` - the object to be formatted into a date/time string. It must be an instance of `Date` or `Number` class.

      `toAppendTo` - the string buffer to be appended with the formatted date/time string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with the formatted date/time string

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if the given object is neither an instance of `Date` class nor an instance of `Number` class

    <!-- -->

    - #### parse

          public Date parse(String text)
                     throws ParseException

      Parses a date/time string into a date.
      Parameters:
      `text` - the date/time string to be parsed

      Returns:
      a `Date` object corresponding to the date/time string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern associated with this formatter is not valid for parsing or the given date/time string cannot be parsed into a `Date` object

    <!-- -->

    - #### parse

          public abstract Date parse(String text,
                                     ParsePosition pos)

      Parses a date/time string into a date, starting from the given parse position.
      Parameters:
      `text` - the date/time string.

      `pos` - indicates where to start the parsing on input. On output, returns where the parse ends if parsing succeeds, or the start index if it fails.

      Returns:
      a `Date` object

    <!-- -->

    - #### parseObject

          public Object parseObject(String text,
                                    ParsePosition pos)

      Parses a date/time string into a (`Date`) object, starting from the given parse position. It is a convenient method which simply calls the `parse(String, ParsePostion)` method.
      Specified by:
      [`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-java.text.ParsePosition-) in class [`Format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      See Also:
      `OraDateFormat.parse(String, ParsePosition)`

    <!-- -->

    - #### getDefaultDateFormatPattern

          public static String getDefaultDateFormatPattern(int style,
                                                           Locale locale)

      Returns the default date format pattern for the given date formatting style and the given locale.
      Parameters:
      `style` - the given date formatting style

      `locale` - the given locale

      Returns:
      the default date format pattern

    <!-- -->

    - #### getDefaultDateFormatPattern

          public static String getDefaultDateFormatPattern(int style,
                                                           OraLocaleInfo localeInfo)

      Returns the default date format pattern for the given date formatting style and the given `OraLocaleInfo` object.
      Parameters:
      `style` - the given date formatting style

      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      the default date format pattern

    <!-- -->

    - #### getDefaultDateTimeFormatPattern

          public static String getDefaultDateTimeFormatPattern(int dateStyle,
                                                               Locale locale)

      Returns the default date/time format pattern for the given date formatting style and the given locale.
      Parameters:
      `dateStyle` - the given date formatting style

      `locale` - the given locale

      Returns:
      the default date/time format pattern

    <!-- -->

    - #### getDefaultDateTimeFormatPattern

          public static String getDefaultDateTimeFormatPattern(int dateStyle,
                                                               OraLocaleInfo localeInfo)

      Returns the default date/time format pattern for the given date formatting style and the given `OraLocaleInfo` object.
      Parameters:
      `dateStyle` - the given date formatting style

      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      the default date/time format pattern

    <!-- -->

    - #### getDefaultTimeFormatPattern

          public static String getDefaultTimeFormatPattern(Locale locale)

      Returns the default time format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      the default time format pattern

    <!-- -->

    - #### getDefaultTimeFormatPattern

          public static String getDefaultTimeFormatPattern(OraLocaleInfo localeInfo)

      Returns the default time format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      the default time format pattern

    <!-- -->

    - #### getCalendar

          public Calendar getCalendar()

      Returns the calendar associated with this date/time formatter.
      Returns:
      the `Calendar` object associated with this formatter

    <!-- -->

    - #### setCalendar

          public void setCalendar(Calendar calendar)

      Sets the given calendar to be used by this date/time formatter.
      Parameters:
      `calendar` - the given `Calendar` object to be used by this formatter

    <!-- -->

    - #### getTimeZone

          public TimeZone getTimeZone()

      Returns the time zone associated with the calendar of this formatter.
      Returns:
      the `TimeZone` object associated with the calendar of this formatter

    <!-- -->

    - #### setTimeZone

          public void setTimeZone(TimeZone timezone)

      Sets the given time zone to be used by the calendar of this formatter.
      Parameters:
      `timezone` - the given `TimeZone` object to be used by the calendar of this formatter

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#clone--) in class [`Format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      Returns:
      a cloned object

    <!-- -->

    - #### equals

          public boolean equals(Object obj)

      Overrides the `equals` method.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `obj` - an object to be compared

      Returns:
      `true` if two objects are identical, otherwise `false`

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

- [Prev Class](OraCollator.md)
- [Next Class](OraDateFormatSymbols.md)

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
