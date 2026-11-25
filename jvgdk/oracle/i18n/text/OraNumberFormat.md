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

- [Prev Class](OraNormalizer.md)
- [Next Class](OraSimpleDateFormat.md)

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

## Class OraNumberFormat

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.text.Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

  - - oracle.i18n.text.OraNumberFormat

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [OraDecimalFormat](OraDecimalFormat.md)

  ------------------------------------------------------------------------



      public abstract class OraNumberFormat
      extends Format

  The `OraNumberFormat` class is an abstract class to do locale-sensitive formatting and parsing between number and string. It supports Oracle number formatting behavior.
  See Also:
  [`OraDecimalFormat`](OraDecimalFormat.md), [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`Format.Field`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.Field.html?is-external=true)

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type   | Field and Description                                        |
    |---------------------|--------------------------------------------------------------|
    | `static int`        | `ALL_FIELD`<br>Constant for `ALL_FIELD` alignment.           |
    | `static int`        | `FRACTION_FIELD`<br>Constant for `FRACTION_FIELD` alignment. |
    | `static int`        | `INTEGER_FIELD`<br>Constant for `INTEGER_FIELD` alignment.   |
    | `protected boolean` | `SQLImplicit`                                                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OraNumberFormat``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                               |
    |--------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                        | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                                                                          | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Overrides the `equals` method.                                                                                                                                                                                                                                                                      |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                        | `format``(`[`BigDecimal`](http://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` number)`<br>Formats a `BigDecimal` object into a string.                                                                                                                                                                                                                                             |
    | `abstract `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`BigDecimal`](http://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` position)`<br>Formats a `BigDecimal` object into a string. |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                        | `format``(`[`BigInteger`](http://docs.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` number)`<br>Formats a `BigInteger` object into a string.                                                                                                                                                                                                                                             |
    | `abstract `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`BigInteger`](http://docs.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` position)`<br>Formats a `BigInteger` object into a string. |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                        | `format``(double number)`<br>Formats a double number into a string.                                                                                                                                                                                                                                                                                                                                                  |
    | `abstract `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(double number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` position)`<br>Formats a double number into a string.                                                                                                      |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                        | `format``(long number)`<br>Formats a long number into a string.                                                                                                                                                                                                                                                                                                                                                      |
    | `abstract `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(long number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` position)`<br>Formats a long number into a string.                                                                                                          |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)            | `format``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` position)`<br>Formats an object into a string.                     |
    | `static OraNumberFormat`                                                                                           | `getCurrencyInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getCurrencyInstance(Locale)`                                                                                                                                                                                                                                                                   |
    | `static OraNumberFormat`                                                                                           | `getCurrencyInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a number formatter that uses the default currency format pattern for the given locale.                                                                                                                                                                                      |
    | `static OraNumberFormat`                                                                                           | `getCurrencyInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a number formatter that uses the default currency format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                  |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultCurrencyFormatPattern``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default currency format pattern for the given locale.                                                                                                                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultCurrencyFormatPattern``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns the default currency format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                                   |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultNumberFormatPattern``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default number format pattern for the given locale.                                                                                                                                                                                                           |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)               | `getDefaultNumberFormatPattern``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns the default number format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                                       |
    | `static OraNumberFormat`                                                                                           | `getInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getInstance(Locale)`                                                                                                                                                                                                                                                                                   |
    | `static OraNumberFormat`                                                                                           | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a number formatter that uses the default currency format pattern for the given locale.                                                                                                                                                                                              |
    | `static OraNumberFormat`                                                                                           | `getInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a number formatter that uses the default currency format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                          |
    | `protected int`                                                                                                    | `getMaximumFractionDigits``()`                                                                                                                                                                                                                                                                                                                                                                                       |
    | `protected int`                                                                                                    | `getMinimumFractionDigits``()`                                                                                                                                                                                                                                                                                                                                                                                       |
    | `protected int`                                                                                                    | `getMinimumIntegerDigits``()`                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static OraNumberFormat`                                                                                           | `getNumberInstance``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getNumberInstance(Locale)`                                                                                                                                                                                                                                                                       |
    | `static OraNumberFormat`                                                                                           | `getNumberInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a number formatter that uses the default number format pattern for the given locale.                                                                                                                                                                                          |
    | `static OraNumberFormat`                                                                                           | `getNumberInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a number formatter that uses the default number format pattern for the given `OraLocaleInfo` object.                                                                                                                                                                                                                      |
    | `static OraNumberFormat`                                                                                           | `getSQLImplicitInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a number formatter that uses the default number format pattern for the given locale and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.                                                                                                                          |
    | `static OraNumberFormat`                                                                                           | `getSQLImplicitInstance``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Returns a number formatter that uses the default number format pattern for the given `OraLocaleInfo` object and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.                                                                                                                                                      |
    | `boolean`                                                                                                          | `isGroupingUsed``()`<br>Checks if the grouping separator is used for this formatter.                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                                          | `isParseIntegerOnly``()`<br>Checks if this formatter parses integer portion only.                                                                                                                                                                                                                                                                                                                                    |
    | [`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)                        | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text)`<br>Parses a string into a number.                                                                                                                                                                                                                                                                      |
    | `abstract `[`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)             | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` parsePosition)`<br>Parses a string into a number, starting from the given parse position.                                                                                                   |
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                        | `parseObject``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` parsePosition)`<br>Parses a string into a (`Number`) object, starting from the given parse position.                                                                                  |
    | `void`                                                                                                             | `setGroupingUsed``(boolean val)`<br>Sets the switch for grouping separator to the given boolean value.                                                                                                                                                                                                                                                                                                               |
    | `protected void`                                                                                                   | `setMaximumFractionDigits``(int max)`                                                                                                                                                                                                                                                                                                                                                                                |
    | `protected void`                                                                                                   | `setMaximumIntegerDigits``(int max)`                                                                                                                                                                                                                                                                                                                                                                                 |
    | `protected void`                                                                                                   | `setMinimumFractionDigits``(int min)`                                                                                                                                                                                                                                                                                                                                                                                |
    | `protected void`                                                                                                   | `setMinimumIntegerDigits``(int min)`                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                             | `setParseIntegerOnly``(boolean val)`<br>Sets the switch for parsing integer only to the given boolean value.                                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-)`, `[`formatToCharacterIterator`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#formatToCharacterIterator-java.lang.Object-)`, `[`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### ALL_FIELD

          public static final int ALL_FIELD

      Constant for `ALL_FIELD` alignment. Used to specify the field position for formatting. The `ALL_FIELD` constant is used to indicate all fields specified in a format pattern.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INTEGER_FIELD

          public static final int INTEGER_FIELD

      Constant for `INTEGER_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FRACTION_FIELD

          public static final int FRACTION_FIELD

      Constant for `FRACTION_FIELD` alignment. Used to specify the field position for formatting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SQLImplicit

          protected boolean SQLImplicit

  <!-- -->

  - ### Constructor Detail

    - #### OraNumberFormat

          public OraNumberFormat()

  <!-- -->

  - ### Method Detail

    - #### getCurrencyInstance

          public static OraNumberFormat getCurrencyInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getCurrencyInstance(Locale)`
      Returns a number formatter that uses the default currency format pattern for the default locale.
      Returns:
      a number formatter

    <!-- -->

    - #### getCurrencyInstance

          public static OraNumberFormat getCurrencyInstance(Locale locale)

      Returns a number formatter that uses the default currency format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      a number formatter

    <!-- -->

    - #### getCurrencyInstance

          public static OraNumberFormat getCurrencyInstance(OraLocaleInfo localeInfo)

      Returns a number formatter that uses the default currency format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a number formatter

    <!-- -->

    - #### getDefaultCurrencyFormatPattern

          public static String getDefaultCurrencyFormatPattern(Locale locale)

      Returns the default currency format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      the default currency format pattern. The format pattern is in the form of ` "<positive pattern>;<negative pattern>"` or, if patterns for both positive and negative patterns are the same, the form is ` "<positive pattern>"`.

    <!-- -->

    - #### getDefaultCurrencyFormatPattern

          public static String getDefaultCurrencyFormatPattern(OraLocaleInfo localeInfo)

      Returns the default currency format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      the default currency format pattern. The format pattern is in the form of ` "<positive pattern>;<negative pattern>"` or, if patterns for both positive and negative patterns are the same, the form is ` "<positive pattern>"`.

    <!-- -->

    - #### getDefaultNumberFormatPattern

          public static String getDefaultNumberFormatPattern(Locale locale)

      Returns the default number format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      the default number format pattern. The format pattern is in the form of ` "<positive pattern>;<negative pattern>"` or, if patterns for both positive and negative patterns are the same, the form is ` "<positive pattern>"`.

    <!-- -->

    - #### getDefaultNumberFormatPattern

          public static String getDefaultNumberFormatPattern(OraLocaleInfo localeInfo)

      Returns the default number format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      the default number format pattern. The format pattern is in the form of ` "<positive pattern>;<negative pattern>"` or, if patterns for both positive and negative patterns are the same, the form is ` "<positive pattern>"`.

    <!-- -->

    - #### getInstance

          public static OraNumberFormat getInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getInstance(Locale)`
      Returns a number formatter that uses the default number format pattern for the default locale.
      Returns:
      a number formatter

    <!-- -->

    - #### getInstance

          public static OraNumberFormat getInstance(Locale locale)

      Returns a number formatter that uses the default currency format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      a number formatter

    <!-- -->

    - #### getInstance

          public static OraNumberFormat getInstance(OraLocaleInfo localeInfo)

      Returns a number formatter that uses the default currency format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a number formatter

    <!-- -->

    - #### getNumberInstance

          public static OraNumberFormat getNumberInstance()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraNumberFormat.getNumberInstance(Locale)`
      Returns a number formatter that uses the default number format pattern for the default locale.
      Returns:
      a number formatter

    <!-- -->

    - #### getNumberInstance

          public static OraNumberFormat getNumberInstance(Locale locale)

      Returns a number formatter that uses the default number format pattern for the given locale.
      Parameters:
      `locale` - the given locale

      Returns:
      a number formatter

    <!-- -->

    - #### getNumberInstance

          public static OraNumberFormat getNumberInstance(OraLocaleInfo localeInfo)

      Returns a number formatter that uses the default number format pattern for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a number formatter

    <!-- -->

    - #### getSQLImplicitInstance

          public static OraNumberFormat getSQLImplicitInstance(Locale locale)

      Returns a number formatter that uses the default number format pattern for the given locale and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.
      Parameters:
      `locale` - the given locale

      Returns:
      a number formatter

    <!-- -->

    - #### getSQLImplicitInstance

          public static OraNumberFormat getSQLImplicitInstance(OraLocaleInfo localeInfo)

      Returns a number formatter that uses the default number format pattern for the given `OraLocaleInfo` object and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

      Returns:
      a number formatter

    <!-- -->

    - #### format

          public String format(BigDecimal number)

      Formats a `BigDecimal` object into a string.
      Parameters:
      `number` - the `BigDecimal` object to be formatted

      Returns:
      a formatted string

    <!-- -->

    - #### format

          public String format(BigInteger number)

      Formats a `BigInteger` object into a string.
      Parameters:
      `number` - the `BigInteger` object to be formatted

      Returns:
      a formatted string

    <!-- -->

    - #### format

          public String format(double number)

      Formats a double number into a string.
      Parameters:
      `number` - the double number to be formatted

      Returns:
      a formatted string

    <!-- -->

    - #### format

          public String format(long number)

      Formats a long number into a string.
      Parameters:
      `number` - the long number to be formatted

      Returns:
      a formatted string

    <!-- -->

    - #### format

          public abstract StringBuffer format(BigDecimal number,
                                              StringBuffer toAppendTo,
                                              FieldPosition position)

      Formats a `BigDecimal` object into a string. Sets field position if it is needed.
      Parameters:
      `number` - the `BigDecimal` object to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `position` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public abstract StringBuffer format(BigInteger number,
                                              StringBuffer toAppendTo,
                                              FieldPosition position)

      Formats a `BigInteger` object into a string. Sets field position if it is needed.
      Parameters:
      `number` - the `BigInteger` object to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `position` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public abstract StringBuffer format(double number,
                                              StringBuffer toAppendTo,
                                              FieldPosition position)

      Formats a double number into a string. Sets field position if it is needed.
      Parameters:
      `number` - the double number to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `position` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public abstract StringBuffer format(long number,
                                              StringBuffer toAppendTo,
                                              FieldPosition position)

      Formats a long number into a string. Sets field position if it is needed.
      Parameters:
      `number` - the long number to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `position` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public StringBuffer format(Object number,
                                     StringBuffer toAppendTo,
                                     FieldPosition position)

      Formats an object into a string. Sets field position if it is needed.
      Specified by:
      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-java.lang.StringBuffer-java.text.FieldPosition-) in class [`Format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      Parameters:
      `number` - the object to be formatted. It must be an instance of `Number` class.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `position` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

      Throws:
      [`IllegalArgumentException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if the given object is not an instance of `Number` class

    <!-- -->

    - #### parse

          public Number parse(String text)
                       throws ParseException

      Parses a string into a number.
      Parameters:
      `text` - the string to be parsed

      Returns:
      a `Number` object corresponding to the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the format pattern associated with this formatter is not valid for parsing or the given string cannot be parsed into a instance of `Number` class

    <!-- -->

    - #### parse

          public abstract Number parse(String text,
                                       ParsePosition parsePosition)

      Parses a string into a number, starting from the given parse position.
      Parameters:
      `text` - the string to be parsed.

      `parsePosition` - indicates where to start the parsing on input. On output, returns where the parse ends if parsing succeeds, or the start index if it fails.

      Returns:
      a `Number` object

    <!-- -->

    - #### parseObject

          public Object parseObject(String text,
                                    ParsePosition parsePosition)

      Parses a string into a (`Number`) object, starting from the given parse position. It is a convenient method which simply calls the `parse(String, ParsePostion)` method.
      Specified by:
      [`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-java.text.ParsePosition-) in class [`Format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      See Also:
      `OraNumberFormat.parse(String, ParsePosition)`

    <!-- -->

    - #### isGroupingUsed

          public boolean isGroupingUsed()

      Checks if the grouping separator is used for this formatter.
      Returns:
      `true` if the grouping separator is used, `false` otherwise

    <!-- -->

    - #### setGroupingUsed

          public void setGroupingUsed(boolean val)

      Sets the switch for grouping separator to the given boolean value.
      Parameters:
      `val` - the given boolean value

    <!-- -->

    - #### isParseIntegerOnly

          public boolean isParseIntegerOnly()

      Checks if this formatter parses integer portion only.
      Returns:
      `true` if this formatter parses integer portion only, `false` otherwise

    <!-- -->

    - #### setParseIntegerOnly

          public void setParseIntegerOnly(boolean val)

      Sets the switch for parsing integer only to the given boolean value.
      Parameters:
      `val` - the given boolean value

    <!-- -->

    - #### setMaximumIntegerDigits

          protected void setMaximumIntegerDigits(int max)

    <!-- -->

    - #### getMinimumIntegerDigits

          protected int getMinimumIntegerDigits()

    <!-- -->

    - #### setMinimumIntegerDigits

          protected void setMinimumIntegerDigits(int min)

    <!-- -->

    - #### getMaximumFractionDigits

          protected int getMaximumFractionDigits()

    <!-- -->

    - #### setMaximumFractionDigits

          protected void setMaximumFractionDigits(int max)

    <!-- -->

    - #### getMinimumFractionDigits

          protected int getMinimumFractionDigits()

    <!-- -->

    - #### setMinimumFractionDigits

          protected void setMinimumFractionDigits(int min)

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
      `true` if two objects are equal, otherwise returns `false`

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

- [Prev Class](OraNormalizer.md)
- [Next Class](OraSimpleDateFormat.md)

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
