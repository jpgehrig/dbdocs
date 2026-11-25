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

- [Prev Class](OraDecimalFormat.md)
- [Next Class](OraNormalizer.md)

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

## Class OraDecimalFormatSymbols

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraDecimalFormatSymbols

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  ------------------------------------------------------------------------



      public final class OraDecimalFormatSymbols
      extends Object
      implements Cloneable, Serializable

  The `OraDecimalFormatSymbols` class is a class that maintains Oracle decimal format symbols such as decimal separator and currency symbols.
  See Also:
  [`OraDecimalFormat`](OraDecimalFormat.md), [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OraDecimalFormatSymbols``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormatSymbols.OraDecimalFormatSymbols(Locale)`                                        |
    | `OraDecimalFormatSymbols``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Constructs an `OraDecimalFormatSymbols` object for the given locale. |
    | `OraDecimalFormatSymbols``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Constructs an `OraDecimalFormatSymbols` object for the given `OraLocaleInfo` object.                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                                                                     |
    |---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                               |
    | `boolean`                                                                                   | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` object)`<br>Overrides the `equals` method.                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getCurrencySymbol``()`<br>Returns the local currency symbol for this object.                                                                                                                                              |
    | `char`                                                                                      | `getDecimalSeparator``()`<br>Returns the decimal separator for this object.                                                                                                                                                |
    | `char`                                                                                      | `getGroupingSeparator``()`<br>Returns the grouping separator for this object.                                                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getInternationalCurrencySymbol``()`<br>Returns the international currency symbol for this object.                                                                                                                         |
    | `int`                                                                                       | `hashCode``()`<br>Overrides the `hashCode` method.                                                                                                                                                                         |
    | `void`                                                                                      | `setCurrencySymbol``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` curSym)`<br>Sets the local currency symbol to the given symbol for this object.                         |
    | `void`                                                                                      | `setDecimalSeparator``(char decSep)`<br>Sets the decimal separator to the given symbol for this object.                                                                                                                    |
    | `void`                                                                                      | `setGroupingSeparator``(char groupSep)`<br>Sets the grouping separator to the given symbol for this object.                                                                                                                |
    | `void`                                                                                      | `setInternationalCurrencySymbol``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` intCurSym)`<br>Sets the international currency symbol to the given symbol for this object. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### OraDecimalFormatSymbols

          public OraDecimalFormatSymbols()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDecimalFormatSymbols.OraDecimalFormatSymbols(Locale)`
      Constructs an `OraDecimalFormatSymbols` object for the default locale.

    <!-- -->

    - #### OraDecimalFormatSymbols

          public OraDecimalFormatSymbols(Locale locale)

      Constructs an `OraDecimalFormatSymbols` object for the given locale.
      Parameters:
      `locale` - the given locale

    <!-- -->

    - #### OraDecimalFormatSymbols

          public OraDecimalFormatSymbols(OraLocaleInfo localeInfo)

      Constructs an `OraDecimalFormatSymbols` object for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

  <!-- -->

  - ### Method Detail

    - #### getCurrencySymbol

          public String getCurrencySymbol()

      Returns the local currency symbol for this object.
      Returns:
      the local currency symbol

    <!-- -->

    - #### setCurrencySymbol

          public void setCurrencySymbol(String curSym)

      Sets the local currency symbol to the given symbol for this object.
      Parameters:
      `curSym` - the given local currency symbol

    <!-- -->

    - #### getDecimalSeparator

          public char getDecimalSeparator()

      Returns the decimal separator for this object.
      Returns:
      the decimal separator

    <!-- -->

    - #### setDecimalSeparator

          public void setDecimalSeparator(char decSep)

      Sets the decimal separator to the given symbol for this object.
      Parameters:
      `decSep` - the given symbol

    <!-- -->

    - #### getGroupingSeparator

          public char getGroupingSeparator()

      Returns the grouping separator for this object.
      Returns:
      the grouping separator

    <!-- -->

    - #### setGroupingSeparator

          public void setGroupingSeparator(char groupSep)

      Sets the grouping separator to the given symbol for this object.
      Parameters:
      `groupSep` - the given symbol

    <!-- -->

    - #### getInternationalCurrencySymbol

          public String getInternationalCurrencySymbol()

      Returns the international currency symbol for this object.
      Returns:
      the international currency symbol

    <!-- -->

    - #### setInternationalCurrencySymbol

          public void setInternationalCurrencySymbol(String intCurSym)

      Sets the international currency symbol to the given symbol for this object.
      Parameters:
      `intCurSym` - the given international currency symbol

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a cloned object

    <!-- -->

    - #### equals

          public boolean equals(Object object)

      Overrides the `equals` method.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

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

- [Prev Class](OraDecimalFormat.md)
- [Next Class](OraNormalizer.md)

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
