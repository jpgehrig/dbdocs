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

- [Prev Class](DBLocaleSource.md)
- [Next Class](LocaleSource.md)

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

## Class HttpAcceptLanguage

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.i18n.servlet.localesource.LocaleSource](LocaleSource.md)

  - - oracle.i18n.servlet.localesource.HttpAcceptLanguage

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class HttpAcceptLanguage
      extends LocaleSource

  The `HttpAcceptLanguage` class is a locale source class that carries the language preference of the web client.
  On each request, the language preferences of the web client are conveyed by the `Accept-Language` item in the HTTP header. The language preference can be composed of multiple locales. For example, when the client sets the language preferences to French, English, German, and Japanese in this order, the `Accept-Language` value would be as follows:

         Accept-Language: en;q=0.9, fr;q=1.0, de, ja


  Considering the locales supported by the application, the `HttpAcceptLanguage` object is instantiated with this value to determine the current user locale. In the preceding example, if the supported locales are `en` and `ja`, the user locale is determined to be `en`, since `fr` and `de` are not supported by the application and `en` has precedence over `ja`. Default Caching : This locale source is not cached in the session by default
  Since:
  10.1.0.2

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`LocaleSource.Alignment`](LocaleSource.Alignment.md)`, `[`LocaleSource.Parameter`](LocaleSource.Parameter.md)`, `[`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.i18n.servlet.localesource.[LocaleSource](LocaleSource.md)

      [`equals`](LocaleSource.md)`, `[`getAttribute`](LocaleSource.md)`, `[`getCharacterSet`](LocaleSource.md)`, `[`getCollator`](LocaleSource.md)`, `[`getCurrencyFormat`](LocaleSource.md)`, `[`getDateFormat`](LocaleSource.md)`, `[`getDateTimeFormat`](LocaleSource.md)`, `[`getISOCurrency`](LocaleSource.md)`, `[`getLocale`](LocaleSource.md)`, `[`getLocaleSourceClass`](LocaleSource.md)`, `[`getNumberFormat`](LocaleSource.md)`, `[`getTimeFormat`](LocaleSource.md)`, `[`getTimeZone`](LocaleSource.md)`, `[`getWritingDirection`](LocaleSource.md)`, `[`hashCode`](LocaleSource.md)`, `[`isCached`](LocaleSource.md)`, `[`isReadOnly`](LocaleSource.md)`, `[`load`](LocaleSource.md)`, `[`setAttribute`](LocaleSource.md)`, `[`setCharacterSet`](LocaleSource.md)`, `[`setCollator`](LocaleSource.md)`, `[`setCurrencyFormat`](LocaleSource.md)`, `[`setDateFormat`](LocaleSource.md)`, `[`setDateTimeFormat`](LocaleSource.md)`, `[`setISOCurrency`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocale`](LocaleSource.md)`, `[`setLocaleSourceClass`](LocaleSource.md)`, `[`setNumberFormat`](LocaleSource.md)`, `[`setTimeFormat`](LocaleSource.md)`, `[`setTimeZone`](LocaleSource.md)`, `[`setWritingDirection`](LocaleSource.md)`, `[`store`](LocaleSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

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

- [Prev Class](DBLocaleSource.md)
- [Next Class](LocaleSource.md)

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
