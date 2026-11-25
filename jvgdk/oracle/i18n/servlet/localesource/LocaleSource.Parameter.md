Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LocaleSource.Alignment.md)
- [Next Class](LocaleSource.WritingDirection.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.i18n.servlet.localesource

## Class LocaleSource.Parameter

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.localesource.LocaleSource.Parameter

<!-- -->

- Enclosing class:
  [LocaleSource](LocaleSource.md)

  ------------------------------------------------------------------------



      public static class LocaleSource.Parameter
      extends Object

  The `LocaleSource.Parameter` class represents locale and attribute variable names.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type               | Field and Description                                          |
    |---------------------------------|----------------------------------------------------------------|
    | `static LocaleSource.Parameter` | `CHARSET`<br>Character set parameter                           |
    | `static LocaleSource.Parameter` | `COMMAND`<br>Command parameter                                 |
    | `static LocaleSource.Parameter` | `CURRENCY_FORMAT`<br>Currency format parameter                 |
    | `static LocaleSource.Parameter` | `DATE_FORMAT`<br>Date format parameter                         |
    | `static LocaleSource.Parameter` | `DATE_TIME_FORMAT`<br>Date and time format parameter           |
    | `static LocaleSource.Parameter` | `ISO_CURRENCY`<br>ISO 4217 currency parameter                  |
    | `static LocaleSource.Parameter` | `LANGUAGE`<br>Language parameter                               |
    | `static LocaleSource.Parameter` | `LINGUISTIC_SORT`<br>Linguistic sorting parameter              |
    | `static LocaleSource.Parameter` | `LOCALE`<br>Locale parameter                                   |
    | `static LocaleSource.Parameter` | `LOCALE_SOURCE`<br>Locale source name parameter                |
    | `static LocaleSource.Parameter` | `LONG_DATE_FORMAT`<br>Long date format parameter               |
    | `static LocaleSource.Parameter` | `LONG_DATE_TIME_FORMAT`<br>Long date and time format parameter |
    | `static LocaleSource.Parameter` | `NUMBER_FORMAT`<br>Number format parameter                     |
    | `static LocaleSource.Parameter` | `TERRITORY`<br>Territory parameter                             |
    | `static LocaleSource.Parameter` | `TIME_FORMAT`<br>Time format parameter                         |
    | `static LocaleSource.Parameter` | `TIMEZONE`<br>Time zone parameter                              |
    | `static LocaleSource.Parameter` | `WRITING_DIRECTION`<br>Writing direction parameter             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                        |
    |---------------------------------------------------------------------------------------------|---------------------------------------------------------------|
    | `int`                                                                                       | `hashCode``()`<br>Returns the hash code for the parameter.    |
    | `static int`                                                                                | `size``()`<br>Returns the number of parameter classes.        |
    | `static LocaleSource.Parameter[]`                                                           | `toArray``()`<br>Returns an array of all parameter objects.   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`<br>Returns the original name of the parameter. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### LOCALE

          public static final LocaleSource.Parameter LOCALE

      Locale parameter

    <!-- -->

    - #### LANGUAGE

          public static final LocaleSource.Parameter LANGUAGE

      Language parameter

    <!-- -->

    - #### TERRITORY

          public static final LocaleSource.Parameter TERRITORY

      Territory parameter

    <!-- -->

    - #### CHARSET

          public static final LocaleSource.Parameter CHARSET

      Character set parameter

    <!-- -->

    - #### TIMEZONE

          public static final LocaleSource.Parameter TIMEZONE

      Time zone parameter

    <!-- -->

    - #### ISO_CURRENCY

          public static final LocaleSource.Parameter ISO_CURRENCY

      ISO 4217 currency parameter

    <!-- -->

    - #### LINGUISTIC_SORT

          public static final LocaleSource.Parameter LINGUISTIC_SORT

      Linguistic sorting parameter

    <!-- -->

    - #### DATE_FORMAT

          public static final LocaleSource.Parameter DATE_FORMAT

      Date format parameter

    <!-- -->

    - #### LONG_DATE_FORMAT

          public static final LocaleSource.Parameter LONG_DATE_FORMAT

      Long date format parameter

    <!-- -->

    - #### TIME_FORMAT

          public static final LocaleSource.Parameter TIME_FORMAT

      Time format parameter

    <!-- -->

    - #### DATE_TIME_FORMAT

          public static final LocaleSource.Parameter DATE_TIME_FORMAT

      Date and time format parameter

    <!-- -->

    - #### LONG_DATE_TIME_FORMAT

          public static final LocaleSource.Parameter LONG_DATE_TIME_FORMAT

      Long date and time format parameter

    <!-- -->

    - #### NUMBER_FORMAT

          public static final LocaleSource.Parameter NUMBER_FORMAT

      Number format parameter

    <!-- -->

    - #### CURRENCY_FORMAT

          public static final LocaleSource.Parameter CURRENCY_FORMAT

      Currency format parameter

    <!-- -->

    - #### WRITING_DIRECTION

          public static final LocaleSource.Parameter WRITING_DIRECTION

      Writing direction parameter

    <!-- -->

    - #### COMMAND

          public static final LocaleSource.Parameter COMMAND

      Command parameter

    <!-- -->

    - #### LOCALE_SOURCE

          public static final LocaleSource.Parameter LOCALE_SOURCE

      Locale source name parameter

  <!-- -->

  - ### Method Detail

    - #### toString

          public String toString()

      Returns the original name of the parameter.
      Overrides:
      [`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      the orignal name of the parameter

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hash code for the parameter.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      the hash value

    <!-- -->

    - #### size

          public static final int size()

      Returns the number of parameter classes.
      Returns:
      the number of parameter classes

    <!-- -->

    - #### toArray

          public static final LocaleSource.Parameter[] toArray()

      Returns an array of all parameter objects.
      Returns:
      array of `Parameter`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LocaleSource.Alignment.md)
- [Next Class](LocaleSource.WritingDirection.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
