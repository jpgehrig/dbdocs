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

- [Prev Class](OraDateFormat.md)
- [Next Class](OraDecimalFormat.md)

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

## Class OraDateFormatSymbols

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraDateFormatSymbols

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Cloneable](http://docs.oracle.com/javase/8/docs/api/java/lang/Cloneable.html?is-external=true)

  ------------------------------------------------------------------------



      public final class OraDateFormatSymbols
      extends Object
      implements Serializable, Cloneable

  The `OraDateFormatSymbols` class is a class that maintains Oracle translations for date/time-related strings such as month names and day-of-the-week names.
  See Also:
  [`OraDateFormat`](OraDateFormat.md), [`OraSimpleDateFormat`](OraSimpleDateFormat.md), [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                         |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OraDateFormatSymbols``()`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormatSymbols.OraDateFormatSymbols(Locale)`                                           |
    | `OraDateFormatSymbols``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Constructs an `OraDateFormatSymbols` object for the given locale. |
    | `OraDateFormatSymbols``(`[`OraLocaleInfo`](../util/OraLocaleInfo.md)` localeInfo)`<br>Constructs an `OraDateFormatSymbols` object for the given `OraLocaleInfo` object.                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)     | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                              |
    | `boolean`                                                                                       | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Overrides the `equals` method.                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getAmPmStrings``()`<br>Returns the meridian indicators for the object.                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getEras``()`<br>Returns the era strings for the object.                                                                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getMonths``()`<br>Returns the month names for the object.                                                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getShortMonths``()`<br>Returns the abbreviated month names for the object.                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getShortWeekdays``()`<br>Returns the abbreviated names of day-of-the-week for the object.                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getWeekdays``()`<br>Returns the names of day-of-the-week for the object.                                                                                                                                                 |
    | `int`                                                                                           | `hashCode``()`<br>Overrides the `hashCode` method.                                                                                                                                                                        |
    | `void`                                                                                          | `setAmPmStrings``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] amPmStrings)`<br>Sets the meridian indicators to the given indicators for this object.                  |
    | `void`                                                                                          | `setEras``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] eras)`<br>Sets the eras to the given eras for this object.                                                     |
    | `void`                                                                                          | `setMonths``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] months)`<br>Sets the month names to the given month names for this object.                                   |
    | `void`                                                                                          | `setShortMonths``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] shortMonths)`<br>Sets the abbreviated month names to the given abbreviated month names for this object. |
    | `void`                                                                                          | `setShortWeekdays``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] shortWeekdays)`<br>Sets the abbreviated names of day-of-the-week to the given names for this object.  |
    | `void`                                                                                          | `setWeekdays``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] weekdays)`<br>Sets the names of day-of-the-week to the given names for this object.                        |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### OraDateFormatSymbols

          public OraDateFormatSymbols()

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraDateFormatSymbols.OraDateFormatSymbols(Locale)`
      Constructs an `OraDateFormatSymbols` object for the default locale.

    <!-- -->

    - #### OraDateFormatSymbols

          public OraDateFormatSymbols(Locale locale)

      Constructs an `OraDateFormatSymbols` object for the given locale.
      Parameters:
      `locale` - the given locale

    <!-- -->

    - #### OraDateFormatSymbols

          public OraDateFormatSymbols(OraLocaleInfo localeInfo)

      Constructs an `OraDateFormatSymbols` object for the given `OraLocaleInfo` object.
      Parameters:
      `localeInfo` - the given `OraLocaleInfo` object

  <!-- -->

  - ### Method Detail

    - #### getEras

          public String[] getEras()

      Returns the era strings for the object. For example, it returns {"bc", "ad"} for en_US.
      Returns:
      the era strings

    <!-- -->

    - #### setEras

          public void setEras(String[] eras)

      Sets the eras to the given eras for this object.
      Parameters:
      `eras` - the given eras.

    <!-- -->

    - #### getMonths

          public String[] getMonths()

      Returns the month names for the object. Months start with January (0) and end with December (11).
      Returns:
      the month names

    <!-- -->

    - #### setMonths

          public void setMonths(String[] months)

      Sets the month names to the given month names for this object. Months start with January (0) and end with December (11).
      Parameters:
      `months` - the given month names

    <!-- -->

    - #### getShortMonths

          public String[] getShortMonths()

      Returns the abbreviated month names for the object. Months start with January (0) and end with December (11).
      Returns:
      the abbreviated month names

    <!-- -->

    - #### setShortMonths

          public void setShortMonths(String[] shortMonths)

      Sets the abbreviated month names to the given abbreviated month names for this object. Months start with January (0) and end with December (11).
      Parameters:
      `shortMonths` - the given abbreviated month names

    <!-- -->

    - #### getWeekdays

          public String[] getWeekdays()

      Returns the names of day-of-the-week for the object. Weekdays start with Sunday (0) and end with Saturday (6).
      Returns:
      the names of day-of-the-week

    <!-- -->

    - #### setWeekdays

          public void setWeekdays(String[] weekdays)

      Sets the names of day-of-the-week to the given names for this object. Weekdays start with Sunday (0) and end with Saturday (6).
      Parameters:
      `weekdays` - the given names of day-of-the-week

    <!-- -->

    - #### getShortWeekdays

          public String[] getShortWeekdays()

      Returns the abbreviated names of day-of-the-week for the object. Weekdays start with Sunday (0) and end with Saturday (6).
      Returns:
      the abbreviated names of day-of-the-week

    <!-- -->

    - #### setShortWeekdays

          public void setShortWeekdays(String[] shortWeekdays)

      Sets the abbreviated names of day-of-the-week to the given names for this object. Weekdays start with Sunday (0) and end with Saturday (6)
      Parameters:
      `shortWeekdays` - the given abbreviated names of day-of-the-week

    <!-- -->

    - #### getAmPmStrings

          public String[] getAmPmStrings()

      Returns the meridian indicators for the object. For example, it returns {"am", "pm"} for en_US.
      Returns:
      the meridian indicators

    <!-- -->

    - #### setAmPmStrings

          public void setAmPmStrings(String[] amPmStrings)

      Sets the meridian indicators to the given indicators for this object.
      Parameters:
      `amPmStrings` - the given meridian indicators.

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

    <!-- -->

    - #### equals

          public boolean equals(Object obj)

      Overrides the `equals` method.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

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

- [Prev Class](OraDateFormat.md)
- [Next Class](OraDecimalFormat.md)

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
