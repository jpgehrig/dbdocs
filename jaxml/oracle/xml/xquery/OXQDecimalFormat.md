Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OXQDebugListener.md)**
- **[Next Class](OXQDynamicContext.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.xquery**

## **Interface OXQDecimalFormat**

-

  ------------------------------------------------------------------------

  **
  **

      public interface OXQDecimalFormat

  **The implementation of this interface should store the decimal format properties that fn:format-number will use to format a number.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                        |
    |--------------------|---------------------------------------------------------------------------------------------------------------|
    | `int`              | `getDecimalSeparator``()`<br>Gets the value of the `decimal-separator` property.                              |
    | `int`              | `getDigit``()`<br>Gets the value of the `digit` property.                                                     |
    | `int`              | `getGroupingSeparator``()`<br>Gets the value of the `grouping-separator` property.                            |
    | `java.lang.String` | `getInfinity``()`<br>Gets the value of the `infinity` property.                                               |
    | `int`              | `getMinusSign``()`<br>Gets the value of the `minus-sign` property.                                            |
    | `java.lang.String` | `getNan``()`<br>Gets the value of the `NaN` property.                                                         |
    | `int`              | `getPatternSeparator``()`<br>Gets the value of the `pattern-separator` property.                              |
    | `int`              | `getPercent``()`<br>Gets the value of the `percent` property.                                                 |
    | `int`              | `getPerMille``()`<br>Gets the value of the `per-mille` property.                                              |
    | `int`              | `getZeroDigit``()`<br>Gets the value of the `zero-digit` property.                                            |
    | `void`             | `setDecimalSeparator``(int decimalSeparatorCodePoint)`<br>Gets the value of the `decimal-separator` property. |
    | `void`             | `setDigit``(int digitCodePoint)`<br>Sets the `digit` property.                                                |
    | `void`             | `setGroupingSeparator``(int groupingSeparatorCodePoint)`<br>Sets the `grouping-separator` property.           |
    | `void`             | `setInfinity``(java.lang.String infinity)`<br>Sets the `inifinty` property.                                   |
    | `void`             | `setMinusSign``(int minusSignCodePoint)`<br>Sets the `minus-sign` property.                                   |
    | `void`             | `setNan``(java.lang.String nan)`<br>Sets the `NaN` (not-a-number) property.                                   |
    | `void`             | `setPatternSeparator``(int patternSeparatorCodePoint)`<br>Sets the `pattern-separator` property.              |
    | `void`             | `setPercent``(int percentCodePoint)`<br>Sets the `percent` property.                                          |
    | `void`             | `setPerMille``(int perMilleCodePoint)`<br>Sets the `per-mille` property.                                      |
    | `void`             | `setZeroDigit``(int zeroDigitCodePoint)`<br>Sets the `zero-digit` property.                                   |

<!-- -->

- - ### Method Detail

    - #### setNan

          void setNan(java.lang.String nan)

      Sets the `NaN` (not-a-number) property. The default value for this property is the string `"NaN"`.
      Parameters:
      `nan` - the string used to represent the double value `NaN`.

    <!-- -->

    - #### getNan

          java.lang.String getNan()

      Gets the value of the `NaN` property. The default value for this property is `"NaN"`.
      Returns:
      the string representing the double value `NaN`.

    <!-- -->

    - #### setInfinity

          void setInfinity(java.lang.String infinity)

      Sets the `inifinty` property. The default value for this property is the string `"Infinity"`.
      Parameters:
      `infinity` - the string used to represent the double value `infinity`.

    <!-- -->

    - #### getInfinity

          java.lang.String getInfinity()

      Gets the value of the `infinity` property. The default value for this property is `"Infinity"`.
      Returns:
      the string representing the double value `infinity`.

    <!-- -->

    - #### setPatternSeparator

          void setPatternSeparator(int patternSeparatorCodePoint)

      Sets the `pattern-separator` property. The default value for this property is the semicolon character `';'`.
      Parameters:
      `patternSeparatorCodePoint` - the codepoint used to separate positive and negative subpictures in a picture string.

    <!-- -->

    - #### getPatternSeparator

          int getPatternSeparator()

      Gets the value of the `pattern-separator` property. The default value for this property is the semicolon character `';'`.
      Returns:
      the codepoint representing the `pattern-separator` property.

    <!-- -->

    - #### setDigit

          void setDigit(int digitCodePoint)

      Sets the `digit` property. The default value for this property is the number sign character `'#'`.
      Parameters:
      `digitCodePoint` - the codepoint used in the picture string to represent an optional digit.

    <!-- -->

    - #### getDigit

          int getDigit()

      Gets the value of the `digit` property. The default value for this property is the number sign character `'#'`
      Returns:
      the codepoint representing the `digit` property.

    <!-- -->

    - #### setZeroDigit

          void setZeroDigit(int zeroDigitCodePoint)
                     throws oracle.xml.xquery.exceptions.XQueryException

      Sets the `zero-digit` property. The default value for this property is the Western digit zero `#x30`. The `zeroDigitCodePoint` parameter must represent a digit and the digit must have the numeric value zero. This property implicitly defines the ten Unicode characters that are used to represent the values 0 to 9. Within the picture string, any of these ten characters can be used (interchangeably) as a placeholder for a mandatory digit. Within the final result string, these ten characters are used to represent the digits zero to nine.
      Parameters:
      `zeroDigitCodePoint` - the codepoint used to represent the digit zero.

      Throws:
      `oracle.xml.xquery.exceptions.XQueryException` - If the `zeroDigitCodePoint` parameter does not represent a digit (category Nd in the Unicode property database) or If the `zeroDigitCodePoint` parameter does not represent the numeric value zero.

    <!-- -->

    - #### getZeroDigit

          int getZeroDigit()

      Gets the value of the `zero-digit` property. The default value for this property is the Western digit zero `#x30`.
      Returns:
      the codepoint representing the `zero-digit` property.

    <!-- -->

    - #### setPerMille

          void setPerMille(int perMilleCodePoint)

      Sets the `per-mille` property. The default value for this property is the Unicode per-mille character `#x2030`.
      Parameters:
      `perMilleCodePoint` - the codepoint used both in the picture string and in the formatted number to indicate that the number is written as a per-thousand fraction.

    <!-- -->

    - #### getPerMille

          int getPerMille()

      Gets the value of the `per-mille` property. The default value for this property is the the Unicode per-mille character `#x2030`.
      Returns:
      the codepoint representing the `per-mille` property.

    <!-- -->

    - #### setPercent

          void setPercent(int percentCodePoint)

      Sets the `percent` property. The default value for this property is the percent character `'%'`.
      Parameters:
      `percentCodePoint` - the codepoint used both in the picture string and in the formatted number to indicate that the number is written as a per-hundred fraction.

    <!-- -->

    - #### getPercent

          int getPercent()

      Gets the value of the `percent` property. The default value for this property is the percent `'%'`.
      Returns:
      the codepoint representing the `percent` property.

    <!-- -->

    - #### setMinusSign

          void setMinusSign(int minusSignCodePoint)
                     throws oracle.xml.xquery.exceptions.XQueryException

      Sets the `minus-sign` property. The default value for this property is the hyphen minus character `#x2D`.
      Parameters:
      `minusSignCodePoint` - the codepoint that represents a single character, which will be used to mark negative numbers.

      Throws:
      `oracle.xml.xquery.exceptions.XQueryException` - If the `minusSignCodePoint` parameter does not represent a single character.

    <!-- -->

    - #### getMinusSign

          int getMinusSign()

      Gets the value of the `minus-sign` property. The default value for this property is the hyphen minus character `#x2D`.
      Returns:
      the codepoint representing the `minus-sign` property.

    <!-- -->

    - #### setGroupingSeparator

          void setGroupingSeparator(int groupingSeparatorCodePoint)

      Sets the `grouping-separator` property. The default value for this property is the comma character `','`.
      Parameters:
      `groupingSeparatorCodePoint` - the codepoint typically used as a thousands separator, both in the picture string and the formated number.

    <!-- -->

    - #### getGroupingSeparator

          int getGroupingSeparator()

      Gets the value of the `grouping-separator` property. The default value for this property is the comma character `','`.
      Returns:
      the codepoint representing the `grouping-separator` property.

    <!-- -->

    - #### setDecimalSeparator

          void setDecimalSeparator(int decimalSeparatorCodePoint)

      Gets the value of the `decimal-separator` property. The default value for this property is the period character `'.'`.
      Parameters:
      `decimalSeparatorCodePoint` - the coidepoint used to separate the integer part of the number from the fractional part, both in the picture string and in the formatted number.

    <!-- -->

    - #### getDecimalSeparator

          int getDecimalSeparator()

      Gets the value of the `decimal-separator` property. The default value for this property is the period character `'.'`.
      Returns:
      the codepoint representing the `decimal-separator` property.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](OXQDebugListener.md)**
- **[Next Class](OXQDynamicContext.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
