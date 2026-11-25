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

- [Prev Class](HttpAcceptLanguage.md)
- [Next Class](LocaleSource.Alignment.md)

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

## Class LocaleSource

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.localesource.LocaleSource

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  <!-- -->

  Direct Known Subclasses:
  [ApplicationDefault](ApplicationDefault.md), [DBLocaleSource](DBLocaleSource.md), [HttpAcceptLanguage](HttpAcceptLanguage.md), [UserInput](UserInput.md)

  ------------------------------------------------------------------------



      public abstract class LocaleSource
      extends Object
      implements Serializable

  The `LocaleSource` class is the abstract base class for locale source objects. A locale source represents an entity that can provide certain locale specific preferences like a locale name, encoding name, etc. There can be many types of sources of pertinent locale preferences, for instance a database table can contain locale specific parameters and can be a locale source. A user action can result in generation of an HTML POST request with query parameters that can be a basis of locale source. Even the HTTP protocol's headers can be yet another source of these locale parameters.
  The user locale is determined according to the list of `LocaleSource` class declarations in the GDK application configuration file. The GDK examines each `LocaleSource` class declaration, in the list using the declared order of the list. The first available `LocaleSource` is used for the user locale.

  The GDK provides the following pre-defined `LocaleSource` implementations:

  - [`HttpAcceptLanguage`](HttpAcceptLanguage.md) - the locale preference set by the web client in the HTTP header.
  - [`UserInput`](UserInput.md) - the locale preference in the parameters of `GET` and `POST` methods.
  - [`DBLocaleSource`](DBLocaleSource.md) - the locale preference stored in the Oracle database.
  - [`ApplicationDefault`](ApplicationDefault.md) - the default locale for the application.

  Note `ApplicationDefault` locale source is implicitly registered in the end of the locale source. If no other locale source is available, the `ApplicationDefault` locale source is used.
  Using the GDK configuration, the language of an application (User Interface) can be configured in many ways. The GDK configuration example below, illustrates configuration for a scenario where the language of an initial application page will be determined based on the language setting of the browser. Additionally, the user will be able to override this language by choosing from the available list of locales displayed in a Locale Selection drop-down. For example, if the browser language setting is Chinese, then pointing your browser to this application will display the User Interface in the Chinese language. Furthermore, the user can select Swiss (German) locale from the Locale Selection dropdown to change the application user interface to display German. The configuration below (from a *gdkapp.xml*) is used by the GDK to first try to use the Accept-Language HTTP header as the source of the locale, unless it is overridden by user input, which in the application's case is the selection of the locale from a Locale Selection dropdown. When the user picks the locale from the dropdown, the JSP posts a *locale* parameter value containing the selected locale. The GDK then sends a response, with the contents in the selected language.

       <locale-determine-rule>
         <locale-source>
           oracle.i18n.servlet.localesource.UserInput
         </locale-source>
         <locale-source>
           oracle.i18n.servlet.localesource.HttpAcceptLanguage
         </locale-source>
       </locale-determine-rule>


  To create a custom locale source object, extend this class. The custom object for instance, may access the Oracle database to fetch and update the user locale preference, or it may access the LDAP server to get and set the language preference elements. Three methods must be implemented in the custom locale source:

  - `public static LocaleSource getInstance(HttpServletRequest)` - used to instantiate the object. It returns the object if it succeeds, otherwise `null`.
  - `public boolean ``LocaleSource.load()` - used to load the locale and its attributes from the locale source.
  - `public boolean ``LocaleSource.store()` - used to store the locale and its attributes into the locale source. If the locale source is read-only, this method should do nothing but return `true`.

  Implement the following method if the locale source can be cached:
  - `public static boolean isAccessible(HttpServletRequest)` - used to check if the locale source is accessible before using the cached object. It returns `true` if the locale source is accessible, otherwise `false`. If this method is not implemented, the GDK assumes that the locale source is always accessible.

  In the constructor, the following parameters must be specified:
  - `cache flag` - indicates whether the locale source can be cached. If the access cost to the locale source is not trivial, such as LDAP server, this flag should be `true`, otherwise `false`.
  - `read-only flag` - indicates whether the locale source is read-only. If the locale source cannot be updated, such as the `Accept-Language` item in the HTTP header, this flag is `true`, otherwise `false`.

  For example, the locale source accessing the LDAP server should be cached so that the GDK keeps the locale information while the user is valid. Once the user logs out, the locale information is no longer valid.
  Since:
  10.1.0.2

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                            |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`LocaleSource.Alignment`](LocaleSource.Alignment.md)<br>The `LocaleSource.Alignment` class represents the alignment of text elements.                           |
    | `static class `   | [`LocaleSource.Parameter`](LocaleSource.Parameter.md)<br>The `LocaleSource.Parameter` class represents locale and attribute variable names.                      |
    | `static class `   | [`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)<br>The `LocaleSource.WritingDirection` class represents the writing direction of the locale. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier     | Constructor and Description                                                                   |
    |--------------|-----------------------------------------------------------------------------------------------|
    | `protected ` | `LocaleSource``(boolean isCached, boolean isReadOnly)`<br>Constructs a `LocaleSource` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                               | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` o)`<br>Determines if a specific object is equal to this object.                                                                                                          |
    | `protected `[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getAttribute``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Returns the attribute object.                                                                                                                             |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)             | `getCharacterSet``()`<br>Returns the character set name in this object.                                                                                                                                                                                                          |
    | [`OraCollator`](../../text/OraCollator.md)                                                              | `getCollator``()`<br>Returns the Oracle collator object.                                                                                                                                                                                                                         |
    | [`OraNumberFormat`](../../text/OraNumberFormat.md)                                                      | `getCurrencyFormat``()`<br>Returns the Oracle currency format in this object.                                                                                                                                                                                                    |
    | [`OraDateFormat`](../../text/OraDateFormat.md)                                                          | `getDateFormat``(int style)`<br>Returns the Oracle date format of the specified style in this object.                                                                                                                                                                            |
    | [`OraDateFormat`](../../text/OraDateFormat.md)                                                          | `getDateTimeFormat``(int style)`<br>Returns the Oracle date and time format of the specified style in this object.                                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)             | `getISOCurrency``()`<br>Returns the ISO 4217 currency ID in this object.                                                                                                                                                                                                         |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)             | `getLocale``()`<br>Returns the `Locale` object in this object.                                                                                                                                                                                                                   |
    | [`Class`](http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)               | `getLocaleSourceClass``()`<br>Returns the locale source class.                                                                                                                                                                                                                   |
    | [`OraNumberFormat`](../../text/OraNumberFormat.md)                                                      | `getNumberFormat``()`<br>Returns the Oracle number format in this object.                                                                                                                                                                                                        |
    | [`OraDateFormat`](../../text/OraDateFormat.md)                                                          | `getTimeFormat``()`<br>Returns the Oracle time format in this object.                                                                                                                                                                                                            |
    | [`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)         | `getTimeZone``()`<br>Returns the time zone in this object.                                                                                                                                                                                                                       |
    | [`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)                                     | `getWritingDirection``()`<br>Returns the writing direction in this object.                                                                                                                                                                                                       |
    | `int`                                                                                                   | `hashCode``()`<br>Returns the hash value of this object.                                                                                                                                                                                                                         |
    | `boolean`                                                                                               | `isCached``()`<br>Checks if the `LocaleSource` object is cached.                                                                                                                                                                                                                 |
    | `boolean`                                                                                               | `isReadOnly``()`<br>Checks if the `LocaleSource` object is read-only.                                                                                                                                                                                                            |
    | `abstract boolean`                                                                                      | `load``()`<br>Loads the locale and all attributes from the actual locale source into this object.                                                                                                                                                                                |
    | `protected void`                                                                                        | `setAttribute``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key, `[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` object)`<br>Registers an attribute object in the locale source. |
    | `void`                                                                                                  | `setCharacterSet``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Registers the Oracle character set name to store in the actual `LocaleSource` class.                                                               |
    | `void`                                                                                                  | `setCollator``(`[`OraCollator`](../../text/OraCollator.md)` ocol)`<br>Registers the Oracle collator to store in the actual `LocaleSource` class.                                                                                                                                 |
    | `void`                                                                                                  | `setCurrencyFormat``(`[`OraNumberFormat`](../../text/OraNumberFormat.md)` nfmt)`<br>Registers the Oracle currency format object to store in the actual `LocaleSource` class.                                                                                                     |
    | `void`                                                                                                  | `setDateFormat``(int style, `[`OraDateFormat`](../../text/OraDateFormat.md)` dtfmt)`<br>Registers the Oracle date format object to store in the actual `LocaleSource` class.                                                                                                     |
    | `void`                                                                                                  | `setDateTimeFormat``(int dtstyle, `[`OraDateFormat`](../../text/OraDateFormat.md)` dtfmt)`<br>Registers the Oracle date time format object to store in the actual `LocaleSource` class.                                                                                          |
    | `void`                                                                                                  | `setISOCurrency``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` currency)`<br>Registers the ISO currency to store in the actual `LocaleSource` class.                                                                            |
    | `void`                                                                                                  | `setLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Registers the `Locale` object with this object.                                                                                                           |
    | `void`                                                                                                  | `setLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale, `[`ApplicationContext`](../ApplicationContext.md)` appctx)`<br>Registers the locale object in this object.                                                    |
    | `void`                                                                                                  | `setLocaleSourceClass``(`[`Class`](http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` loccls)`<br>Registers the locale source class object.                                                                                                        |
    | `void`                                                                                                  | `setNumberFormat``(`[`OraNumberFormat`](../../text/OraNumberFormat.md)` nfmt)`<br>Registers the Oracle number format object to store in the actual `LocaleSource` class.                                                                                                         |
    | `void`                                                                                                  | `setTimeFormat``(`[`OraDateFormat`](../../text/OraDateFormat.md)` tmfmt)`<br>Registers the Oracle time format object to store in the actual `LocaleSource` class.                                                                                                                |
    | `void`                                                                                                  | `setTimeZone``(`[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz)`<br>Registers the `TimeZone` ID to store in the actual `LocaleSource` class.                                                                                |
    | `void`                                                                                                  | `setWritingDirection``(`[`LocaleSource.WritingDirection`](LocaleSource.WritingDirection.md)` wdir)`<br>Registers the writing direction to store in the actual `LocaleSource` class.                                                                                              |
    | `abstract boolean`                                                                                      | `store``()`<br>Stores the locale and all attributes of the object in the actual `LocaleSource` class.                                                                                                                                                                            |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Constructor Detail

    - #### LocaleSource

          protected LocaleSource(boolean isCached,
                                 boolean isReadOnly)

      Constructs a `LocaleSource` object.
      Parameters:
      `isCached` - `true` if the locale source can be cached

      `isReadOnly` - `true` if the locale source is read-only

  <!-- -->

  - ### Method Detail

    - #### isCached

          public final boolean isCached()

      Checks if the `LocaleSource` object is cached.
      Returns:
      `true` if this object is cached; `false` otherwise.

    <!-- -->

    - #### isReadOnly

          public final boolean isReadOnly()

      Checks if the `LocaleSource` object is read-only.
      If this is `true`, creation and update operations on this object are omitted.

      Returns:
      `true` if this object is read-only; `false` otherwise.

    <!-- -->

    - #### store

          public abstract boolean store()

      Stores the locale and all attributes of the object in the actual `LocaleSource` class.
      This method must be implemented by the concrete classes.

      Returns:
      `true` if the storing operation is successful; `false` otherwise

    <!-- -->

    - #### load

          public abstract boolean load()

      Loads the locale and all attributes from the actual locale source into this object.
      This method must be implemented by the concrete classes.

      Returns:
      `true` if the loading operation is successful; `false` otherwise

    <!-- -->

    - #### setLocale

          public final void setLocale(Locale locale)

      Registers the `Locale` object with this object.
      Parameters:
      `locale` - the `Locale` object

    <!-- -->

    - #### setLocale

          public final void setLocale(Locale locale,
                                      ApplicationContext appctx)

      Registers the locale object in this object.
      Parameters:
      `locale` - the `Locale` object

      `appctx` - the `ApplicationContext` object

    <!-- -->

    - #### setISOCurrency

          public final void setISOCurrency(String currency)

      Registers the ISO currency to store in the actual `LocaleSource` class.
      Parameters:
      `currency` - the ISO currency ID defined in ISO 4217

    <!-- -->

    - #### setCharacterSet

          public final void setCharacterSet(String charset)

      Registers the Oracle character set name to store in the actual `LocaleSource` class.
      Parameters:
      `charset` - the Oracle character set name

    <!-- -->

    - #### setLocaleSourceClass

          public final void setLocaleSourceClass(Class loccls)

      Registers the locale source class object.
      Parameters:
      `loccls` - a `Class` object

    <!-- -->

    - #### setTimeZone

          public final void setTimeZone(TimeZone tz)

      Registers the `TimeZone` ID to store in the actual `LocaleSource` class. For example: ` America/Los_Angeles`
      Parameters:
      `tz` - a `TimeZone` object to register

    <!-- -->

    - #### setDateTimeFormat

          public final void setDateTimeFormat(int dtstyle,
                                              OraDateFormat dtfmt)

      Registers the Oracle date time format object to store in the actual `LocaleSource` class.
      Parameters:
      `dtstyle` - the date format style defined in the `OraDateFormat` class

      `dtfmt` - an `OraDateFormat` object

    <!-- -->

    - #### setDateFormat

          public final void setDateFormat(int style,
                                          OraDateFormat dtfmt)

      Registers the Oracle date format object to store in the actual `LocaleSource` class.
      Parameters:
      `style` - the date format style defined in the `OraDateFormat` class

      `dtfmt` - an `OraDateFormat` object

    <!-- -->

    - #### setTimeFormat

          public final void setTimeFormat(OraDateFormat tmfmt)

      Registers the Oracle time format object to store in the actual `LocaleSource` class.
      Parameters:
      `tmfmt` - an `OraDateFormat` object

    <!-- -->

    - #### setWritingDirection

          public final void setWritingDirection(LocaleSource.WritingDirection wdir)

      Registers the writing direction to store in the actual `LocaleSource` class.
      Parameters:
      `wdir` - a writing direction of text on display

    <!-- -->

    - #### setCurrencyFormat

          public final void setCurrencyFormat(OraNumberFormat nfmt)

      Registers the Oracle currency format object to store in the actual `LocaleSource` class.
      Parameters:
      `nfmt` - an `OraNumberFormat` object to register

    <!-- -->

    - #### setNumberFormat

          public final void setNumberFormat(OraNumberFormat nfmt)

      Registers the Oracle number format object to store in the actual `LocaleSource` class.
      Parameters:
      `nfmt` - an `OraNumberFormat` object to register

    <!-- -->

    - #### setCollator

          public final void setCollator(OraCollator ocol)

      Registers the Oracle collator to store in the actual `LocaleSource` class.
      Parameters:
      `ocol` - an `OraCollator` object to register

    <!-- -->

    - #### setAttribute

          protected final void setAttribute(String key,
                                            Object object)

      Registers an attribute object in the locale source.
      Used in the concrete classes to set custom attributes.
      Note the attribute object must be `Serializable`.

      Parameters:
      `key` - a `String` key of object

      `object` - an object

    <!-- -->

    - #### getLocale

          public final Locale getLocale()

      Returns the `Locale` object in this object.
      Returns:
      `Locale` object

    <!-- -->

    - #### getISOCurrency

          public final String getISOCurrency()

      Returns the ISO 4217 currency ID in this object.
      Returns:
      the ISO 4217 currency ID

    <!-- -->

    - #### getCharacterSet

          public final String getCharacterSet()

      Returns the character set name in this object.
      Returns:
      the character set name

    <!-- -->

    - #### getLocaleSourceClass

          public final Class getLocaleSourceClass()

      Returns the locale source class.
      Returns:
      the locale source class

    <!-- -->

    - #### getTimeZone

          public final TimeZone getTimeZone()

      Returns the time zone in this object.
      Returns:
      a `TimeZone` object

    <!-- -->

    - #### getDateTimeFormat

          public final OraDateFormat getDateTimeFormat(int style)

      Returns the Oracle date and time format of the specified style in this object.
      Parameters:
      `style` - the `Date` format style

      Returns:
      an `OraDateFormat` object

    <!-- -->

    - #### getDateFormat

          public final OraDateFormat getDateFormat(int style)

      Returns the Oracle date format of the specified style in this object.
      Parameters:
      `style` - the `Date` format style

      Returns:
      an `OraDateFormat` object

    <!-- -->

    - #### getTimeFormat

          public final OraDateFormat getTimeFormat()

      Returns the Oracle time format in this object.
      Returns:
      the Oracle time format

    <!-- -->

    - #### getWritingDirection

          public final LocaleSource.WritingDirection getWritingDirection()

      Returns the writing direction in this object.
      Returns:
      a `WritingDirection` object

    <!-- -->

    - #### getCurrencyFormat

          public final OraNumberFormat getCurrencyFormat()

      Returns the Oracle currency format in this object.
      Returns:
      an `OraNumberFormat` object

    <!-- -->

    - #### getNumberFormat

          public final OraNumberFormat getNumberFormat()

      Returns the Oracle number format in this object.
      Returns:
      an `OraNumberFormat` object

    <!-- -->

    - #### getCollator

          public final OraCollator getCollator()

      Returns the Oracle collator object.
      Returns:
      an `OraCollator` object

    <!-- -->

    - #### getAttribute

          protected final Object getAttribute(String key)

      Returns the attribute object.
      Used in the concrete classes to retrieve custom attributes. Note the attribute object must be `Serializable`.

      Parameters:
      `key` - a `String` key of object

      Returns:
      an `Object` associated with the `key`

    <!-- -->

    - #### equals

          public boolean equals(Object o)

      Determines if a specific object is equal to this object.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `o` - an `Object` to be compared

      Returns:
      boolean `true` if the objects are equal; `false` otherwise

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hash value of this object.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      hash value

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

- [Prev Class](HttpAcceptLanguage.md)
- [Next Class](LocaleSource.Alignment.md)

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
