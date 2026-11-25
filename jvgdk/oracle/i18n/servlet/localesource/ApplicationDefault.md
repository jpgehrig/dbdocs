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

- Prev Class
- [Next Class](DBLocaleSource.md)

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

## Class ApplicationDefault

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.i18n.servlet.localesource.LocaleSource](LocaleSource.md)

  - - oracle.i18n.servlet.localesource.ApplicationDefault

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  ------------------------------------------------------------------------



      public class ApplicationDefault
      extends LocaleSource

  The `ApplicationDefault` class is the default locale source class that represents the default locale and attributes used in the application. If in the GDK configuration file, no locale determination rules are defined or if they are defined but not available, this class acts as the default locale source. The default locale source does not need to be explicitly declared, since it is implicitly understood to be the default. Additionally, the default locale value for the ApplicationDefault locale source can be overridden in the GDK configuration via the use of the `default` attribute of the `locale` tag. In the example below the default application locale value is begin set to the Chinese locale:
        <application-locales>
            <locale>de-CH</locale>
            <locale>en-US</locale>
            <locale default="yes">zh-CN</locale>
        </application-locales>


  All data in this object is filled by the [`ApplicationContext`](../ApplicationContext.md) class during the initialization process. The values cannot be changed until the application is shut down. Default Caching : This locale source is cached in the ApplicationContext by default.

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

- Prev Class
- [Next Class](DBLocaleSource.md)

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
