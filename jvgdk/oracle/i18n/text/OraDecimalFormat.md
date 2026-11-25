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

- [Prev Class](OraDateFormatSymbols.md)
- [Next Class](OraDecimalFormatSymbols.md)

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

## Class OraDecimalFormat

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.text.Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

  - - [oracle.i18n.text.OraNumberFormat](OraNumberFormat.md)

    - - oracle.i18n.text.OraDecimalFormat

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OraDecimalFormat
      extends OraNumberFormat

  The `OraDecimalFormat` class is a concrete class to do locale-sensitive formatting and parsing between number and string. It supports Oracle number formatting behavior.
  See Also:
  [`OraNumberFormat`](OraNumberFormat.md), [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`Format.Field`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.Field.html?is-external=true)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.i18n.text.[OraNumberFormat](OraNumberFormat.md)

      [`ALL_FIELD`](OraNumberFormat.md)`, `[`FRACTION_FIELD`](OraNumberFormat.md)`, `[`INTEGER_FIELD`](OraNumberFormat.md)`, `[`SQLImplicit`](OraNumberFormat.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OraDecimalFormat``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormat.OraDecimalFormat(String, OraDecimalFormatSymbols)`                                                                                                                                         |
    | `OraDecimalFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormat.OraDecimalFormat(String, OraDecimalFormatSymbols)`                                    |
    | `OraDecimalFormat``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern, `[`OraDecimalFormatSymbols`](OraDecimalFormatSymbols.md)` symbols)`<br>Constructs an `OraDecimalFormat` object using the given format pattern and the given decimal format symbols. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                    |
    |---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                  | `applyPattern``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pattern)`<br>Modifies this formatter by using the given format pattern.                                                                                                                                                                                                                                     |
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)             | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                               | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` object)`<br>Overrides the `equals` method.                                                                                                                                                                                                                                                                        |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`BigDecimal`](http://docs.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats a `BigDecimal` object into a string. |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(`[`BigInteger`](http://docs.oracle.com/javase/8/docs/api/java/math/BigInteger.html?is-external=true)` number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats a `BigInteger` object into a string. |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(double number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats a double number into a string.                                                                                                      |
    | [`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true) | `format``(long number, `[`StringBuffer`](http://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html?is-external=true)` toAppendTo, `[`FieldPosition`](http://docs.oracle.com/javase/8/docs/api/java/text/FieldPosition.html?is-external=true)` fieldPosition)`<br>Formats a long number into a string.                                                                                                          |
    | [`OraDecimalFormatSymbols`](OraDecimalFormatSymbols.md)                                                 | `getOraDecimalFormatSymbols``()`<br>Returns the Oracle decimal format symbols used in this formatter.                                                                                                                                                                                                                                                                                                                     |
    | `int`                                                                                                   | `hashCode``()`<br>Overrides the `hashCode` method.                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                                                               | `isDecimalSeparatorAlwaysShown``()`<br>Returns `true` if decimal separator is always shown in the result string.                                                                                                                                                                                                                                                                                                          |
    | [`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)             | `parse``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` text, `[`ParsePosition`](http://docs.oracle.com/javase/8/docs/api/java/text/ParsePosition.html?is-external=true)` parsePosition)`<br>Parses a string into a `Number` object, starting from the given parse position.                                                                                               |
    | `void`                                                                                                  | `setDecimalSeparatorAlwaysShown``(boolean val)`<br>Sets the switch for decimal separator to the given boolean value.                                                                                                                                                                                                                                                                                                      |
    | `protected void`                                                                                        | `setMaximumFractionDigits``(int val)`                                                                                                                                                                                                                                                                                                                                                                                     |
    | `protected void`                                                                                        | `setMaximumIntegerDigits``(int val)`                                                                                                                                                                                                                                                                                                                                                                                      |
    | `protected void`                                                                                        | `setMinimumFractionDigits``(int val)`                                                                                                                                                                                                                                                                                                                                                                                     |
    | `protected void`                                                                                        | `setMinimumIntegerDigits``(int val)`                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setOraDecimalFormatSymbols``(`[`OraDecimalFormatSymbols`](OraDecimalFormatSymbols.md)` sym)`<br>Sets this formatter to use the given Oracle decimal format symbols.                                                                                                                                                                                                                                                      |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)             | `toPattern``()`<br>Returns a format pattern string that represents the formatting behavior of this formatter.                                                                                                                                                                                                                                                                                                             |

    - ### Methods inherited from class oracle.i18n.text.[OraNumberFormat](OraNumberFormat.md)

      [`format`](OraNumberFormat.md)`, `[`format`](OraNumberFormat.md)`, `[`format`](OraNumberFormat.md)`, `[`format`](OraNumberFormat.md)`, `[`format`](OraNumberFormat.md)`, `[`getCurrencyInstance`](OraNumberFormat.md)`, `[`getCurrencyInstance`](OraNumberFormat.md)`, `[`getCurrencyInstance`](OraNumberFormat.md)`, `[`getDefaultCurrencyFormatPattern`](OraNumberFormat.md)`, `[`getDefaultCurrencyFormatPattern`](OraNumberFormat.md)`, `[`getDefaultNumberFormatPattern`](OraNumberFormat.md)`, `[`getDefaultNumberFormatPattern`](OraNumberFormat.md)`, `[`getInstance`](OraNumberFormat.md)`, `[`getInstance`](OraNumberFormat.md)`, `[`getInstance`](OraNumberFormat.md)`, `[`getMaximumFractionDigits`](OraNumberFormat.md)`, `[`getMinimumFractionDigits`](OraNumberFormat.md)`, `[`getMinimumIntegerDigits`](OraNumberFormat.md)`, `[`getNumberInstance`](OraNumberFormat.md)`, `[`getNumberInstance`](OraNumberFormat.md)`, `[`getNumberInstance`](OraNumberFormat.md)`, `[`getSQLImplicitInstance`](OraNumberFormat.md)`, `[`getSQLImplicitInstance`](OraNumberFormat.md)`, `[`isGroupingUsed`](OraNumberFormat.md)`, `[`isParseIntegerOnly`](OraNumberFormat.md)`, `[`parse`](OraNumberFormat.md)`, `[`parseObject`](OraNumberFormat.md)`, `[`setGroupingUsed`](OraNumberFormat.md)`, `[`setParseIntegerOnly`](OraNumberFormat.md)

    <!-- -->

    - ### Methods inherited from class java.text.[Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true)

      [`format`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#format-java.lang.Object-)`, `[`formatToCharacterIterator`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#formatToCharacterIterator-java.lang.Object-)`, `[`parseObject`](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true#parseObject-java.lang.String-)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### OraDecimalFormat

          public OraDecimalFormat()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormat.OraDecimalFormat(String, OraDecimalFormatSymbols)`
      Constructs an `OraDecimalFormat` object using the default number format pattern and the default decimal format symbols for the default locale.

    <!-- -->

    - #### OraDecimalFormat

          public OraDecimalFormat(String pattern)
                           throws ParseException

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormat.OraDecimalFormat(String, OraDecimalFormatSymbols)`
      Constructs an `OraDecimalFormat` object using the given format pattern and the default decimal format symbols for the default locale.
      Parameters:
      `pattern` - the given format pattern, if null, uses the default number format pattern for the default locale and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the given pattern is invalid

    <!-- -->

    - #### OraDecimalFormat

          public OraDecimalFormat(String pattern,
                                  OraDecimalFormatSymbols symbols)
                           throws ParseException

      Constructs an `OraDecimalFormat` object using the given format pattern and the given decimal format symbols.
      Parameters:
      `pattern` - the give format pattern, if null, uses the default number format pattern for the default locale and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.

      `symbols` - the given decimal format symbols

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the given pattern is invalid

  <!-- -->

  - ### Method Detail

    - #### applyPattern

          public void applyPattern(String pattern)
                            throws ParseException

      Modifies this formatter by using the given format pattern. The given format pattern should be specified as:
            "<positive pattern>[;<negative pattern>]"

      This means that a positive format pattern must be present but a negative format pattern is optional. If there is no negative pattern given, the positive pattern with a leading minus sign is used for formatting or parsing negative numbers.
      Parameters:
      `pattern` - given format pattern, if null, uses the default number format pattern for the default locale and supports SQL TO_CHAR()/TO_NUMBER() implicit conversion.

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the given pattern is invalid

    <!-- -->

    - #### format

          public StringBuffer format(BigDecimal number,
                                     StringBuffer toAppendTo,
                                     FieldPosition fieldPosition)

      Formats a `BigDecimal` object into a string. Sets field position if it is needed.
      Specified by:
      [`format`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Parameters:
      `number` - the `BigDecimal` object to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public StringBuffer format(BigInteger number,
                                     StringBuffer toAppendTo,
                                     FieldPosition fieldPosition)

      Formats a `BigInteger` object into a string. Sets field position if it is needed.
      Specified by:
      [`format`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Parameters:
      `number` - the `BigInteger` object to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public StringBuffer format(double number,
                                     StringBuffer toAppendTo,
                                     FieldPosition fieldPosition)

      Formats a double number into a string. Sets field position if it is needed.
      Specified by:
      [`format`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Parameters:
      `number` - the double number to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### format

          public StringBuffer format(long number,
                                     StringBuffer toAppendTo,
                                     FieldPosition fieldPosition)

      Formats a long number into a string. Sets field position if it is needed.
      Specified by:
      [`format`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Parameters:
      `number` - the long number to be formatted.

      `toAppendTo` - the string buffer to be appended with the formatted string.

      `fieldPosition` - to be used to get offsets of a given field in the returned string buffer. On input, the alignment field of which the offsets are to be returned. On output, the offsets of the alignment field in the returned string buffer.

      Returns:
      the string buffer appended with a formatted string

    <!-- -->

    - #### parse

          public Number parse(String text,
                              ParsePosition parsePosition)

      Parses a string into a `Number` object, starting from the given parse position.
      Specified by:
      [`parse`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Parameters:
      `text` - the string

      `parsePosition` - indicates where to start the parsing on input. On output, returns where the parse ends if parsing succeeds, or the start index if it fails.

      Returns:
      a `Number` object

    <!-- -->

    - #### isDecimalSeparatorAlwaysShown

          public boolean isDecimalSeparatorAlwaysShown()

      Returns `true` if decimal separator is always shown in the result string.
      Returns:
      a boolean value

    <!-- -->

    - #### setDecimalSeparatorAlwaysShown

          public void setDecimalSeparatorAlwaysShown(boolean val)

      Sets the switch for decimal separator to the given boolean value.
      Parameters:
      `val` - the given boolean value

    <!-- -->

    - #### getOraDecimalFormatSymbols

          public OraDecimalFormatSymbols getOraDecimalFormatSymbols()

      Returns the Oracle decimal format symbols used in this formatter.
      Returns:
      an `OraDecimalFormatSymbols` object

      See Also:
      [`OraDecimalFormatSymbols`](OraDecimalFormatSymbols.md)

    <!-- -->

    - #### setOraDecimalFormatSymbols

          public void setOraDecimalFormatSymbols(OraDecimalFormatSymbols sym)

      Sets this formatter to use the given Oracle decimal format symbols.
      Parameters:
      `sym` - the given Oracle decimal format symbols

    <!-- -->

    - #### toPattern

          public String toPattern()

      Returns a format pattern string that represents the formatting behavior of this formatter.
      Returns:
      a format pattern string

    <!-- -->

    - #### setMaximumIntegerDigits

          protected void setMaximumIntegerDigits(int val)

      Overrides:
      [`setMaximumIntegerDigits`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

    <!-- -->

    - #### setMinimumIntegerDigits

          protected void setMinimumIntegerDigits(int val)

      Overrides:
      [`setMinimumIntegerDigits`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

    <!-- -->

    - #### setMaximumFractionDigits

          protected void setMaximumFractionDigits(int val)

      Overrides:
      [`setMaximumFractionDigits`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

    <!-- -->

    - #### setMinimumFractionDigits

          protected void setMinimumFractionDigits(int val)

      Overrides:
      [`setMinimumFractionDigits`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

      Returns:
      a cloned object

    <!-- -->

    - #### equals

          public boolean equals(Object object)

      Overrides the `equals` method.
      Overrides:
      [`equals`](OraNumberFormat.md) in class [`OraNumberFormat`](OraNumberFormat.md)

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
      a hash value for the object

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

- [Prev Class](OraDateFormatSymbols.md)
- [Next Class](OraDecimalFormatSymbols.md)

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
