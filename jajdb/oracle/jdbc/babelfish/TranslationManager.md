Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TranslationManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishStatement.md)
- [Next Class](Translator.md)

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

oracle.jdbc.babelfish

## Class TranslationManager

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.jdbc.babelfish.TranslationManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class TranslationManager
      extends Object

  Provides the translator for a connection. Automatically manages finding a translation cache for the connection conditions. If a cache is not avaialble it creates a new cache and attaches it to the translator.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `TranslationManager``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                      | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`Translator`](Translator.md) | `getTranslator``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` connectionURL, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` translationProfile, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` localErrorTranslationFilePath)`<br>Get the query and error translator with an internal reference to the translation cache if one is available for the unique url, user and translation profile combination or a new cache if its not available. |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### TranslationManager

          public TranslationManager()

  <!-- -->

  - ### Method Detail

    - #### getTranslator

          public static Translator getTranslator(String connectionURL,
                                                 String user,
                                                 String translationProfile,
                                                 String localErrorTranslationFilePath)
                                          throws SQLException

      Get the query and error translator with an internal reference to the translation cache if one is available for the unique url, user and translation profile combination or a new cache if its not available.
      Parameters:
      `connectionURL` - the connection URL string for the connection

      `user` - the username for the connection

      `translationProfile` - The Translation profile

      `localErrorTranslationFilePath` - Path to the XML file defining the error translations for the case when connection cannot be established to the server and thus the translations cannot happen on the server

      Returns:
      the translator object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - thrown if the the local error file cannot be parsed

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TranslationManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishStatement.md)
- [Next Class](Translator.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
