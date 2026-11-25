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

- Prev Class
- [Next Class](Localizer.md)

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

oracle.i18n.servlet

## Class ApplicationContext

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.ApplicationContext

<!-- -->

-

  ------------------------------------------------------------------------



      public class ApplicationContext
      extends Object

  The `ApplicationContext` class provides an application with a globalization configuration environment and controls application scope operations in the GDK framework.
  Generally in a J2EE based application, the application code does not need to explicitly create an `ApplicationContext` object, but rather retrieves an instance by calling the [`ServletHelper.getApplicationContextInstance(HttpServletRequest)`](ServletHelper.md) method. In JSP/Servlet based applications, the ApplicationContext is driven by the GDK Application Configuration file *gdkapp.xml*. The elements of the configuration file, for example: `application-locales`, `page-charset`, `locale-charset-maps`, etc... map to methods in this class. To better understand the various configuration elements, see the *The GDK Application Configuration File* section of the *Globalization Development Guidelines* document.

  An instance of this object must be created at startup time of the application either by the [`ContextListener`](listener/ContextListener.md) object or in a custom context listener for Java/JSP server applications and be registered in the servlet context with the key `ApplicationContext.OBJECT`.

  Since:
  10.1.0.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                                                                    | Field and Description                                                                            |
    |------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `DEFAULT_GDKAPP`<br>The Constant for the name of the default GDK application configuration file. |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `OBJECT_KEY`<br>Constant for the key name used to retrieve the ApplicationContext object.        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ApplicationContext``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` pathToConfigFile)`<br>Constructs an ApplicationContext object based on the specified application configuration InputStream.                                                                                                                                               |
    | `ApplicationContext``(`[`InputStream`](http://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` pathToConfigFile, `[`ClassLoader`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassLoader.html?is-external=true)` cloader)`<br>Constructs an ApplicationContext object based on the specified application configuration InputStream and the `ClassLoader` object. |
    | `ApplicationContext``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pathToConfigFile)`<br>Constructs an ApplicationContext object that is based on a specified GDK application configuration file.                                                                                                                                                    |
    | `ApplicationContext``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pathToConfigFile, `[`ClassLoader`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassLoader.html?is-external=true)` cloader)`<br>Constructs an ApplicationContext object that is based on a specified GDK application configuration file and the `ClassLoader` object.      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)     | `fallbackLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Validates if the locale supplied as an argument is supported.                  |
    | [`LocaleSource`](localesource/LocaleSource.md)                                                  | `getApplicationDefaultLocaleSource``()`<br>Returns the application default locale source instance.                                                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getIANAPageCharacterSet``()`<br>Returns the default IANA page character set name of the application or returns the string `AUTO-CHARSET`.                                                                 |
    | [`Class`](http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`[]`   | `getLocaleSources``()`<br>Returns an array of locale source Class objects that are used to determine the current locale.                                                                                   |
    | [`Map`](http://docs.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)           | `getMessageBundle``()`<br>Returns a `Map` consisting of message bundle name and message bundle object pairs.                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getParameterName``(`[`LocaleSource.Parameter`](localesource/LocaleSource.Parameter.md)` parameter)`<br>Returns a `String` representing the parameter name used to specify locale attributes.              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getSupportedIANACharacterSets``()`<br>Returns an array of supported IANA character set names.                                                                                                             |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)`[]` | `getSupportedLocales``()`<br>Returns an array of locales supported by the application.                                                                                                                     |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getSupportedOraLanguages``()`<br>Returns supported Oracle languages based on the application locale list.                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getSupportedOraLanguages``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraTerritory)`<br>Returns supported Oracle languages for the Oracle territory.   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getSupportedOraTerritories``()`<br>Returns the supported Oracle territories.                                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getSupportedOraTerritories``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage)`<br>Returns supported Oracle territories for the Oracle language. |
    | `int`                                                                                           | `hashCode``()`<br>Returns the hash value.                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### OBJECT_KEY

          public static final String OBJECT_KEY

      Constant for the key name used to retrieve the ApplicationContext object.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_GDKAPP

          public static final String DEFAULT_GDKAPP

      The Constant for the name of the default GDK application configuration file.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ApplicationContext

          public ApplicationContext(String pathToConfigFile)
                             throws ClassNotFoundException,
                                    PatternSyntaxException,
                                    UnsupportedEncodingException

      Constructs an ApplicationContext object that is based on a specified GDK application configuration file. The `ClassLoader` object is derived from this object.
      Note: Do not use this method for a JSP/Java Servlet application, instead, use the [`ServletHelper.getApplicationContextInstance(HttpServletRequest)`](ServletHelper.md) method.

      Parameters:
      `pathToConfigFile` - an absolute file path of the application configuration file

      Throws:
      [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true) - if the `LocaleSource` class is not found

      [`PatternSyntaxException`](http://docs.oracle.com/javase/8/docs/api/java/util/regex/PatternSyntaxException.html?is-external=true) - if rewriting rule or locale to charset mapping regular expression is invalid

      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if character set is invalid

    <!-- -->

    - #### ApplicationContext

          public ApplicationContext(InputStream pathToConfigFile)
                             throws ClassNotFoundException,
                                    PatternSyntaxException,
                                    UnsupportedEncodingException

      Constructs an ApplicationContext object based on the specified application configuration InputStream.
      Parameters:
      `pathToConfigFile` - an input stream object that references the application configuration file

      Throws:
      [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true) - if the `LocaleSource` class is not found

      [`PatternSyntaxException`](http://docs.oracle.com/javase/8/docs/api/java/util/regex/PatternSyntaxException.html?is-external=true) - if rewriting rule or locale to charset mapping regular expression is invalid

      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if character set is invalid

    <!-- -->

    - #### ApplicationContext

          public ApplicationContext(String pathToConfigFile,
                                    ClassLoader cloader)
                             throws ClassNotFoundException,
                                    PatternSyntaxException,
                                    UnsupportedEncodingException

      Constructs an ApplicationContext object that is based on a specified GDK application configuration file and the `ClassLoader` object. The class loader may be required when a custom `LocaleSource` object is used in the application configuration file.
      Note: Do not use this method for a JSP/Java Servlet application, instead, use the [`ServletHelper.getApplicationContextInstance(HttpServletRequest)`](ServletHelper.md) method.

      Parameters:
      `pathToConfigFile` - an absolute file path of the application configuration file

      `cloader` - the `ClassLoader` object that will be used to load [`LocaleSource`](localesource/LocaleSource.md) classes and message bundles.

      Throws:
      [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true) - if the `LocaleSource` class is not found

      [`PatternSyntaxException`](http://docs.oracle.com/javase/8/docs/api/java/util/regex/PatternSyntaxException.html?is-external=true) - if rewriting rule or locale to charset mapping regular expression is invalid

      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if character set is invalid

    <!-- -->

    - #### ApplicationContext

          public ApplicationContext(InputStream pathToConfigFile,
                                    ClassLoader cloader)
                             throws ClassNotFoundException,
                                    PatternSyntaxException,
                                    UnsupportedEncodingException

      Constructs an ApplicationContext object based on the specified application configuration InputStream and the `ClassLoader` object. The class loader is required if you will be using a custom `LocaleSource` object that is specified in the GDK application configuration file.
      Parameters:
      `pathToConfigFile` - an input stream object that references the application configuration file

      `cloader` - the `ClassLoader` object that will be used to load [`LocaleSource`](localesource/LocaleSource.md) classes and message bundles.

      Throws:
      [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true) - if the `LocaleSource` class is not found

      [`PatternSyntaxException`](http://docs.oracle.com/javase/8/docs/api/java/util/regex/PatternSyntaxException.html?is-external=true) - if rewriting rule or locale to charset mapping regular expression is invalid

      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true) - if character set is invalid

  <!-- -->

  - ### Method Detail

    - #### getIANAPageCharacterSet

          public String getIANAPageCharacterSet()

      Returns the default IANA page character set name of the application or returns the string `AUTO-CHARSET`. If the value `AUTO-CHARSET` is set, this implies that the GDK framework automatically assigns an appropriate character set value based on the locale.
      If the `AUTO-CHARSET` value is set, you may retrieve the resolved character set name by using the [`Localizer.getIANACharacterSet()`](Localizer.md) method.

      Returns:
      an IANA character set name or `AUTO-CHARSET`

    <!-- -->

    - #### getParameterName

          public String getParameterName(LocaleSource.Parameter parameter)

      Returns a `String` representing the parameter name used to specify locale attributes. For example, if you want to get the locale value, use the `LocaleSource.Parameter.LOCALE` object as input. For example:
           ApplicationContext appctx = ServletHelper.getApplicationContextInstance(
             request);
           String locale = request.getParameter(
             appctx.getParameterName(LocaleSource.Parameter.LOCALE));


      Parameters:
      `parameter` - a parameter type

      Returns:
      a parameter name used in the application

    <!-- -->

    - #### getLocaleSources

          public Class[] getLocaleSources()

      Returns an array of locale source Class objects that are used to determine the current locale.
      Returns:
      an array of [`LocaleSource`](localesource/LocaleSource.md) Class objects

    <!-- -->

    - #### getApplicationDefaultLocaleSource

          public LocaleSource getApplicationDefaultLocaleSource()

      Returns the application default locale source instance.
      Returns:
      a [`LocaleSource`](localesource/LocaleSource.md) representing the application default locale

    <!-- -->

    - #### getMessageBundle

          public Map getMessageBundle()

      Returns a `Map` consisting of message bundle name and message bundle object pairs.
      Returns:
      the map of the message bundle object where the key is the message bundle name and the value is the [`ResourceBundle`](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html?is-external=true) object

    <!-- -->

    - #### getSupportedLocales

          public Locale[] getSupportedLocales()

      Returns an array of locales supported by the application.
      The supported locale can be specified in the application configuration file.

      Returns:
      an array of `Locale` objects representing supported locales in the application

    <!-- -->

    - #### getSupportedOraLanguages

          public String[] getSupportedOraLanguages(String oraTerritory)

      Returns supported Oracle languages for the Oracle territory.
      The supported languages are determined by the supported locale. If the given territory name is `null`, all supported Oracle languages are returned.

      Parameters:
      `oraTerritory` - Oracle territory name. If this parameter is null, then the method will return all supported Oracle languages that are based on the application locale list.

      Returns:
      an array of `String` representing the supported languages in the application

    <!-- -->

    - #### getSupportedOraLanguages

          public String[] getSupportedOraLanguages()

      Returns supported Oracle languages based on the application locale list.
      The supported languages are determined by the supported locale.

      Returns:
      an array of `String` objects representing the supported languages in the application

    <!-- -->

    - #### getSupportedOraTerritories

          public String[] getSupportedOraTerritories(String oraLanguage)

      Returns supported Oracle territories for the Oracle language.
      The supported territories are determined by the supported locale list. If the given language is `null`, all available territories are returned.

      Parameters:
      `oraLanguage` - Oracle language name

      Returns:
      an array of `String` representing the supported territories in the application

    <!-- -->

    - #### getSupportedOraTerritories

          public String[] getSupportedOraTerritories()

      Returns the supported Oracle territories.
      The supported territories are determined by the supported locale list.

      Returns:
      an array of `String` representing the supported territories in the application

    <!-- -->

    - #### getSupportedIANACharacterSets

          public String[] getSupportedIANACharacterSets()

      Returns an array of supported IANA character set names. This list is based on the supported locale list.
      Returns:
      an array of supported IANA character sets in the application

    <!-- -->

    - #### fallbackLocale

          public Locale fallbackLocale(Locale locale)

      Validates if the locale supplied as an argument is supported. If the locale is supported, it is returned by the method. Otherwise, the fallback locale is returned.
      If you are not sure that the given locale is supported, call this method the custom locale source object.

      Note that supported locales in the application are not equivalent to the translation locales that are handled by the [`ResourceBundle`](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html?is-external=true) class or the [`ServletHelper.rewriteURL(String, HttpServletRequest)`](ServletHelper.md) method. They validate locales by checking the actual translation resources. If the given locale's translation exists, it is returned, otherwise, it returns the fallback locale's translation.

      Parameters:
      `locale` - a `Locale` object to be examined

      Returns:
      a `Locale` that is supported by the application

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hash value.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      hash value

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

- Prev Class
- [Next Class](Localizer.md)

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
