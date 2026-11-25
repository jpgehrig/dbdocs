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

- [Prev Class](LocaleMapper.md)
- [Next Class](OraLocaleInfo.md)

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

## Class OraDisplayLocaleInfo

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.OraDisplayLocaleInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraDisplayLocaleInfo
      extends Object

  The `OraDisplayLocaleInfo` class is a utility class that provides predefined translations for locale related attributes. These attributes can be items like the display name for locales, languages, character sets, timezones, etc.
  To use the services of this class, first an `OraDisplayLocaleInfo` object should be instantiated by calling the `OraDisplayLocaleInfo.getInstance(java.util.Locale)` method. The `getInstance()` method takes a `Locale` parameter that controls the translation language of any locale display items that are retrieved via the API. The example below shows how to retrieve a German translation for the Java timezone identifier *America/Los_Angeles*:

           ...

           OraDisplayLocaleInfo odli = OraDisplayLocaleInfo.getInstance(Locale.GERMANY);
           TimeZone tz = TimeZone.getTimeZone("America/Los_Angeles");

           // tzName will contain the localized time zone string in German.
           String tzName = odli.getDisplayTimeZone(tz);


  Since:
  10.1.0.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                  |
    |-------------------|------------------------------------------------------------------------|
    | `static int`      | `DEFAULT`<br>Constant value to specify the `DEFAULT` formatting style. |
    | `static int`      | `LONG`<br>Constant value to specify the `LONG` formatting style.       |
    | `static int`      | `SHORT`<br>Constant value to specify the `SHORT` formatting style.     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                          | Method and Description                                                                                                                                                                                                                                                                                                                              |
    |------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][]` | `getAvailableLanguages``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns the available language IDs along with their corresponding display names sorted in the translated display name order.                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][]` | `getAvailableTerritories``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns the available territory IDs along with their corresponding display names sorted in the display name order.                                                                                        |
    | `static `[`List`](http://docs.oracle.com/javase/8/docs/api/java/util/List.html?is-external=true)           | `getCommonLocales``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns a list of the common locales sorted by the translated names.                                                                                                                                             |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayCharacterSet``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Returns a translated character set name.                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayCountry``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated country or territory name.                                                                                                                                                                      |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayCountry``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` country)`<br>Returns a translated country or territory name.                                                                                                                                                                     |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayCurrency``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` currencySymbol)`<br>Returns a translated currency name.                                                                                                                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayLanguage``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated language name.                                                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayLanguage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns a translated language name.                                                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayLinguisticSort``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` linguisticSort)`<br>Returns a translated linguistic sorting name.                                                                                                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated locale name for the passed in locale parameter.                                                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayLocale``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraTerritory)`<br>Returns a translated locale name for the passed in language/territory combination.                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayTerritory``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns a translated country or territory name.                                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayTimeZone``(int style, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tzs)`<br>Returns a translated time zone name.                                                                                                                                                                        |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayTimeZone``(int style, `[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz)`<br>Returns a translated time zone name.                                                                                                                                                                     |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayTimeZone``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` tzs)`<br>Returns a translated time zone name.                                                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                | `getDisplayTimeZone``(`[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz)`<br>Returns a translated time zone name.                                                                                                                                                                                |
    | `static OraDisplayLocaleInfo`                                                                              | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` transLocale)`<br>Constructs or reuses an instance of the `OraDisplayLocaleInfo` class associated with the translation locale.                                                                                                          |
    | `static OraDisplayLocaleInfo`                                                                              | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` transLocale, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` defLocale)`<br>Constructs or reuses an instance of the `OraDisplayLocaleInfo` class associated with the translation locale. |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)                | `getLocale``()`<br>Returns the locale associated with this object.                                                                                                                                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### SHORT

          public static final int SHORT

      Constant value to specify the `SHORT` formatting style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LONG

          public static final int LONG

      Constant value to specify the `LONG` formatting style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT

          public static final int DEFAULT

      Constant value to specify the `DEFAULT` formatting style.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getLocale

          public Locale getLocale()

      Returns the locale associated with this object. This locale is the translation locale, i.e. the locale (language) to which the display names are translated.
      Returns:
      a Java `Locale` object

    <!-- -->

    - #### getInstance

          public static OraDisplayLocaleInfo getInstance(Locale transLocale)

      Constructs or reuses an instance of the `OraDisplayLocaleInfo` class associated with the translation locale.
      Parameters:
      `transLocale` - a translation locale

      Returns:
      an instance of the `OraDisplayLocaleInfo` class

    <!-- -->

    - #### getInstance

          public static OraDisplayLocaleInfo getInstance(Locale transLocale,
                                                         Locale defLocale)

      Constructs or reuses an instance of the `OraDisplayLocaleInfo` class associated with the translation locale. Uses the passed in default locale for fallback mechanism, if necessary.
      Parameters:
      `transLocale` - a translation locale

      `defLocale` - the default locale

      Returns:
      an instance of `OraDisplayLocaleInfo` class

    <!-- -->

    - #### getDisplayLocale

          public String getDisplayLocale(Locale locale)

      Returns a translated locale name for the passed in locale parameter. The translation language used for translation is determined by the translation locale that was specified to retrieve an instance of this object.
      Parameters:
      `locale` - a locale to be translated

      Returns:
      a translated locale name

    <!-- -->

    - #### getDisplayLocale

          public String getDisplayLocale(String oraLanguage,
                                         String oraTerritory)

      Returns a translated locale name for the passed in language/territory combination.
      Parameters:
      `oraLanguage` - an Oracle language name

      `oraTerritory` - an Oracle territory name

      Returns:
      a translated locale name

    <!-- -->

    - #### getDisplayLanguage

          public String getDisplayLanguage(Locale locale)

      Returns a translated language name.
      Parameters:
      `locale` - a locale that includes the language to be translated

      Returns:
      a translated language name

    <!-- -->

    - #### getDisplayLanguage

          public String getDisplayLanguage(String language)

      Returns a translated language name.
      Parameters:
      `language` - an ISO based or Oracle language name

      Returns:
      a translated language name

    <!-- -->

    - #### getDisplayCountry

          public String getDisplayCountry(Locale locale)

      Returns a translated country or territory name.
      Parameters:
      `locale` - a locale that includes the country to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayCountry

          public String getDisplayCountry(String country)

      Returns a translated country or territory name.
      Parameters:
      `country` - an ISO based or Oracle country name to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayTerritory

          public String getDisplayTerritory(String territory)

      Returns a translated country or territory name.
      Parameters:
      `territory` - a country name to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayTimeZone

          public String getDisplayTimeZone(TimeZone tz)

      Returns a translated time zone name.
      If the translation is not found, the return value is composed by using the return value of the `getRawOffset` method in the form of `(`**`UTC`**`SHH:MM)` where `S` represents the sign of the value, `HH` represents the hours of the offset, and `MI` represents the minutes of the offset.

      Parameters:
      `tz` - a time zone to be translated

      Returns:
      a translated time zone name

    <!-- -->

    - #### getDisplayTimeZone

          public String getDisplayTimeZone(String tzs)

      Returns a translated time zone name.
      Parameters:
      `tzs` - a Java based time zone ID to be translated. If the time zone ID is invalid, `UTC` is used

      Returns:
      a translated time zone name

      See Also:
      `OraDisplayLocaleInfo.getDisplayTimeZone(TimeZone)`

    <!-- -->

    - #### getDisplayTimeZone

          public String getDisplayTimeZone(int style,
                                           TimeZone tz)

      Returns a translated time zone name.
      Parameters:
      `style` - the format style, for example, `SHORT`, `LONG`, or `DEFAULT`

      `tz` - a time zone to be translated

      Returns:
      a translated time zone name

      See Also:
      `OraDisplayLocaleInfo.getDisplayTimeZone(TimeZone)`

    <!-- -->

    - #### getDisplayTimeZone

          public String getDisplayTimeZone(int style,
                                           String tzs)

      Returns a translated time zone name.
      Parameters:
      `style` - the format style, for example, `SHORT`, `LONG`, or `DEFAULT`

      `tzs` - a Java based time zone ID to be translated. If the time zone ID is invalid, `UTC` is used

      Returns:
      a translated time zone name

      See Also:
      `OraDisplayLocaleInfo.getDisplayTimeZone(TimeZone)`

    <!-- -->

    - #### getDisplayLinguisticSort

          public String getDisplayLinguisticSort(String linguisticSort)

      Returns a translated linguistic sorting name.
      Parameters:
      `linguisticSort` - an Oracle linguistic sorting name to be translated

      Returns:
      a translated linguistic sorting name

    <!-- -->

    - #### getDisplayCharacterSet

          public String getDisplayCharacterSet(String charset)

      Returns a translated character set name.
      Parameters:
      `charset` - a character set name to be translated. The name can either be an IANA or Oracle based name.

      Returns:
      a translated character set name

    <!-- -->

    - #### getDisplayCurrency

          public String getDisplayCurrency(String currencySymbol)

      Returns a translated currency name.
      Parameters:
      `currencySymbol` - a character set symbol ISO 4217

      Returns:
      a translated currency name

    <!-- -->

    - #### getCommonLocales

          public static List getCommonLocales(Locale translocale)

      Returns a list of the common locales sorted by the translated names. The common locale list is a subset of the "available" locales that the GDK supports.
      Parameters:
      `translocale` - the translation locale

      Returns:
      a common `Locale` object list

    <!-- -->

    - #### getAvailableLanguages

          public static String[][] getAvailableLanguages(Locale translocale)

      Returns the available language IDs along with their corresponding display names sorted in the translated display name order.
      Parameters:
      `translocale` - the translation locale

      Returns:
      a sorted 2-dimensional array of available languages. The returned array has the structure of: {{ "language ID 1", "language ID 2", "language ID 3", ... }, { "display name 1", "display name 2", "display name 3", ... }} The first element is an array of available language IDs sorted based on the order of their translated display names. The second element is an array of the corresponding translated display names. In other words, for the returned array lang\[\]\[\], lang\[0\]\[i\] is a language ID and lang\[1\]\[i\] contains its corresponding translated display name.

    <!-- -->

    - #### getAvailableTerritories

          public static String[][] getAvailableTerritories(Locale translocale)

      Returns the available territory IDs along with their corresponding display names sorted in the display name order.
      Parameters:
      `translocale` - the translation locale

      Returns:
      a sorted 2-dimensional array of available territories. The returned array has the structure of: {{ "territory ID 1", "territory ID 2", "territory ID 3", ... }, { "display name 1", "display name 2", "display name 3", ... }} The first element is an array of available territory IDs sorted based on the order of their translated display names. The second element is an array of the corresponding translated display names. In other words, for the returned array terr\[\]\[\], terr\[0\]\[i\] is a territory ID and terr\[1\]\[i\] contains its corresponding translated display name.

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

- [Prev Class](LocaleMapper.md)
- [Next Class](OraLocaleInfo.md)

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
