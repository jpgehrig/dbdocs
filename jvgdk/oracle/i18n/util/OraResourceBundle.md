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

- [Prev Class](OraLocaleInfo.md)
- [Next Class](OraSQLUtil.md)

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

oracle.i18n.util

## Class OraResourceBundle

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.OraResourceBundle

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraResourceBundle
      extends Object

  The `OraResourceBundle` class is the factory class that constructs a `java.util.ResourceBundle` instance.
  This class provides the special locale fallback behaviors on top of the Java behaviors. The rules follow:

  - If the given locale exactly matches the locale in the available resource bundles, it will be used.
  - If the resource bundle for Chinese in Singapore (`zh_SG`) is not found, it will fallback to the resource bundle for Chinese in China (`zh_CN`) for Simplified Chinese translations.
  - If the resource bundle for Chinese in Hong Kong (`zh_HK`) is not found, it will fallback to the resource bundle for Chinese in Taiwan (`zh_TW`) for Traditional Chinese translations.
  - If the resource bundle for Chinese in Macau (`zh_MO`) is not found, it will fallback to the resource bundle for Chinese in Taiwan (`zh_TW`) for Traditional Chinese translations.
  - If the resource bundles for any other Chinese locale (`zh_` and `zh`) is not found, it will fallback to the resource bundle for Chinese in China (`zh_CN`) for Simplified Chinese translations.
  - The default locale, which can be obtained by the `Locale.getDefault()` method, will not be considered in the fallback operations.

  For example, assume the default locale is `ja_JP` and the resource bundle for it is available. When the resource bundle for `es_MX` is requested and neither resource bundle for `es` or `es_MX` is provided, the base resource bundle object that does not have a local suffix is returned.

  The usage of the `OraResourceBundle` class is similar to the `java.util.ResourceBundle` class, but the `OraResourceBundle` class does not instantiate itself. Instead, the return value of the `getBundle` method is an instance of the subclass of the `java.util.ResourceBundle` class. The following is an example showing how to get the instance of the bundle:

       import java.util.ResourceBundle;
       import oracle.i18n.util.OraResourceBundle;
       ...
       ResourceBundle resb = OraResourceBundle.getBundle(
         "oracle.demo.wob.Translations", request.getLocale());
       ...
       String resb = resb.getString("hello");
       ...


  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`ResourceBundle`](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html?is-external=true) | `getBundle``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseName)`<br>Deprecated. <br>As of Oracle Database 10g Release 2 (10.2), replaced by `OraResourceBundle.getBundle(String, Locale)`                                                                                                                                                                          |
    | `static `[`ResourceBundle`](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html?is-external=true) | `getBundle``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseName, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a `ResourceBundle` object specified by the base class name.                                                                                                                      |
    | `static `[`ResourceBundle`](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html?is-external=true) | `getBundle``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseName, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale, `[`ClassLoader`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassLoader.html?is-external=true)` classLoader)`<br>Returns a `ResourceBundle` object specified by the base class name. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### getBundle

          public static ResourceBundle getBundle(String baseName,
                                                 Locale locale,
                                                 ClassLoader classLoader)

      Returns a `ResourceBundle` object specified by the base class name. A locale should be specified to get the translations. The class loader can be specified if necessary.
      Parameters:
      `baseName` - a base name of the `ResourceBundle` class

      `locale` - a locale used to specify the translation language

      `classLoader` - a `ClassLoader` object used to load the `ResourceBundle` class

      Returns:
      a `ResourceBundle` object

    <!-- -->

    - #### getBundle

          public static ResourceBundle getBundle(String baseName,
                                                 Locale locale)

      Returns a `ResourceBundle` object specified by the base class name. A locale should be specified to get the translations.
      Parameters:
      `baseName` - a base name of the `ResourceBundle` class

      `locale` - a locale used to specify the translation language

      Returns:
      a `ResourceBundle` object

    <!-- -->

    - #### getBundle

          public static ResourceBundle getBundle(String baseName)

      Deprecated. As of Oracle Database 10g Release 2 (10.2), replaced by `OraResourceBundle.getBundle(String, Locale)`
      Returns a `ResourceBundle` object derived from the given base class name. By default, the translation is in English.
      Parameters:
      `baseName` - a base name of the `ResourceBundle` class

      Returns:
      a `ResourceBundle` object

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

- [Prev Class](OraLocaleInfo.md)
- [Next Class](OraSQLUtil.md)

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
