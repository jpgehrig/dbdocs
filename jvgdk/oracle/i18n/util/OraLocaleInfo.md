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

- [Prev Class](OraDisplayLocaleInfo.md)
- [Next Class](OraResourceBundle.md)

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

## Class OraLocaleInfo

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.OraLocaleInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraLocaleInfo
      extends Object

  The `OraLocaleInfo` is a utility class that provides locale related information regarding locale attributes like language, territory, character set, timezone, collators, etc... Additionally it exposes methods that provide lists for available and common locale attributes. This class can be used in conjunction with the [`OraDisplayLocaleInfo`](OraDisplayLocaleInfo.md) class to provide localized names for the various attributes.
  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                            | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)                  | `clone``()`<br>Overrides the `clone` method.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                                                    | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj)`<br>Overrides the `equals` method.                                                                                                                                                                                                                                                                                                           |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableCharacterSets``()`<br>Returns a list of the available Oracle character sets.                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableCurrencies``()`<br>Returns a list of the available ISO 4217 currencies.                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableDBCharacterSets``()`<br>Returns a list of the available database character set names depending on whether the platform is ascii-based or ebcdic-based.                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableLanguages``()`<br>Returns a list of the available Oracle languages, i.e. languages supported by the GDK.                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][]`   | `getAvailableLanguages``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns the available language IDs along with their corresponding display names sorted in the translated display name order.                                                                                                                                                                                      |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableLinguisticSorts``()`<br>Returns a list of the available Oracle linguistic sorts.                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableLocale``()`<br>Returns the available Oracle locale list.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableNationalCharacterSets``()`<br>Returns a list of the available national character sets.                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getAvailableTerritories``()`<br>Returns a list of the available Oracle territories.                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][]`   | `getAvailableTerritories``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns the available territory IDs along with their corresponding display names sorted in the display name order.                                                                                                                                                                                              |
    | `static `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)`[]`     | `getCommonLocales``()`<br>Returns the common locale list, i.e. locales that are commonly used.                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)`[]`     | `getCommonLocales``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` translocale)`<br>Returns the common locale list that is sorted based on the given translation locale.                                                                                                                                                                                                                                   |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getCommonTimeZoneIDs``()`<br>Returns the common time zone IDs in an array.                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)`[]` | `getCommonTimeZones``()`<br>Returns the common time zone list.                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `getCurrencySymbol``()`<br>Returns the currency symbol for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getCurrencySymbol``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` iso4217code)`<br>Returns the currency symbol based on the given ISO 4217 code.                                                                                                                                                                                                                                                         |
    | `static OraLocaleInfo`                                                                                       | `getDefault``()`<br>Returns the default `OraLocaleInfo` instance based on the Oracle default locale.                                                                                                                                                                                                                                                                                                                                                      |
    | `static OraLocaleInfo`                                                                                       | `getInstance``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Retrieves an instance of the OraLocaleInfo object for the given Java `Locale` object.                                                                                                                                                                                                                                            |
    | `static OraLocaleInfo`                                                                                       | `getInstance``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Retrieves an instance of the OraLocaleInfo object for the given language and territory.                                                                                                                               |
    | `static OraLocaleInfo`                                                                                       | `getInstance``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` linguisticSort)`<br>Retrieves an instance of the OraLocaleInfo object for the given language, territory and sort parameter. |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `getLanguage``()`<br>Returns the Oracle language name for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `getLinguisticSort``()`<br>Returns the Oracle linguistic sorting name for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalCharacterSets``()`<br>Returns the common Oracle character sets based on the language of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalCharacterSets``(int platform)`<br>Returns the common Oracle character sets based on the language of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                               |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalCharacterSets``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns the common Oracle character sets based on the given language.                                                                                                                                                                                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalCharacterSets``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language, int platform)`<br>Returns the common Oracle character sets based on the given language.                                                                                                                                                                                                                                  |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][]`   | `getLocalCommonCharacterSets``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns the common Oracle character sets based on the given language.                                                                                                                                                                                                                                          |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalCurrencies``()`<br>Returns the common ISO 4217 currency based on the territory of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalCurrencies``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns the common ISO 4217 currency codes based on the given territory.                                                                                                                                                                                                                                               |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)                  | `getLocale``()`<br>Returns the Java `Locale` corresponding to this object.                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)         | `getLocaleFromString``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` localestring)`<br>Retrieves a Java `Locale` object that maps to the ISO locale string.                                                                                                                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalLanguages``()`<br>Returns the common Oracle languages based on the territory of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalLanguages``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns the common Oracle languages based on the given territory.                                                                                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalLinguisticSorts``()`<br>Returns the common linguistic sorts based on the language of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                              |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalLinguisticSorts``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns the common linguistic sorts based on the given language.                                                                                                                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`              | `getLocalTerritories``()`<br>Returns the common Oracle territories based on the language of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalTerritories``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns the common Oracle territories based on the given language.                                                                                                                                                                                                                                                     |
    | [`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)`[]`          | `getLocalTimeZones``()`<br>Returns the common time zone list for the territory of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)`[]` | `getLocalTimeZones``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns the common time zone list for the given Oracle territory.                                                                                                                                                                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getRecommendedDBCharacterSets``()`<br>Returns an alphabetically sorted list of the recommended database character set names depending on whether the platform is ASCII-based or EBCDIC-based.                                                                                                                                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `getShortLanguage``()`<br>Returns Oracle short language name for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                           |
    | `int`                                                                                                        | `getStartDayOfTheWeek``()`<br>Returns the start day-of-the-week for the object.                                                                                                                                                                                                                                                                                                                                                                           |
    | `static int`                                                                                                 | `getStartDayOfTheWeek``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns the start day of the week for the given Oracle territory for the object.                                                                                                                                                                                                                                     |
    | `static int`                                                                                                 | `getStartDayOfTheWeek``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns the start day of the week for the given Oracle language and Oracle territory for the object.                                                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `getTerritory``()`<br>Returns the Oracle territory name for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                                |
    | `int`                                                                                                        | `getWritingDirection``()`<br>Returns the Oracle writing direction for this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                                                                                        | `hashCode``()`<br>Overrides the `hashCode` method.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                  | `toString``()`<br>Returns the string representation of this `OraLocaleInfo` instance.                                                                                                                                                                                                                                                                                                                                                                     |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### getInstance

          public static OraLocaleInfo getInstance(String language,
                                                  String territory,
                                                  String linguisticSort)

      Retrieves an instance of the OraLocaleInfo object for the given language, territory and sort parameter.
      Parameters:
      `language` - the Oracle language name or the ISO language code

      `territory` - the Oracle territory name or an ISO country code. The language and territory (country) must either both be Oracle based names or ISO based names. They must not be mixed and matched

      `linguisticSort` - the Oracle linguistic sort rule name

      Returns:
      an `OraLocaleInfo` instance or null if either language or territory is not a legal name or ISO code

      Throws:
      [`IllegalStateException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalStateException.html?is-external=true) - if the linguistic sort definition is broken

    <!-- -->

    - #### getInstance

          public static OraLocaleInfo getInstance(String language,
                                                  String territory)

      Retrieves an instance of the OraLocaleInfo object for the given language and territory. Uses the default sorting rule for this locale.
      Parameters:
      `language` - the Oracle language name or the ISO language code

      `territory` - the Oracle territory name or an ISO country code. The language and territory (country) must either both be Oracle based names or ISO based names. They must not be mixed and matched

      Returns:
      an `OraLocaleInfo` instance or null if either language or territory is not a legal name or ISO code

    <!-- -->

    - #### getInstance

          public static OraLocaleInfo getInstance(Locale locale)

      Retrieves an instance of the OraLocaleInfo object for the given Java `Locale` object.
      Parameters:
      `locale` - Java `Locale` object

      Returns:
      an `OraLocaleInfo` instance

    <!-- -->

    - #### getLocale

          public Locale getLocale()

      Returns the Java `Locale` corresponding to this object.
      Returns:
      Java `Locale`

    <!-- -->

    - #### getLanguage

          public String getLanguage()

      Returns the Oracle language name for this `OraLocaleInfo` instance.
      Returns:
      the Oracle language name

    <!-- -->

    - #### getTerritory

          public String getTerritory()

      Returns the Oracle territory name for this `OraLocaleInfo` instance.
      Returns:
      the Oracle territory name

    <!-- -->

    - #### getLinguisticSort

          public String getLinguisticSort()

      Returns the Oracle linguistic sorting name for this `OraLocaleInfo` instance. If the sorting name is "BINARY", it will be suffixed by "-" plus oracle character set name to distinguish among different character sets. This function gets the default value from the language definition directly. But this value is often not valid for some languages. It is recommended to use [`LocaleMapper.getOraLinguisticSortFromLocale(Locale)`](LocaleMapper.md) to get the default linguistic sorting name for a locale.
      Returns:
      the Oracle linguistic name

    <!-- -->

    - #### getWritingDirection

          public int getWritingDirection()

      Returns the Oracle writing direction for this `OraLocaleInfo` instance.
      Returns:
      the writing direction: `0 = LEFT to RIGHT, 1=RIGHT to LEFT`

    <!-- -->

    - #### getShortLanguage

          public String getShortLanguage()

      Returns Oracle short language name for this `OraLocaleInfo` instance.
      Returns:
      a short Oracle language name

    <!-- -->

    - #### getLocalCharacterSets

          public String[] getLocalCharacterSets()

      Returns the common Oracle character sets based on the language of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCharacterSet` method to find its translation.
      Note the common character sets vary among platforms. This method returns the list for Unix platforms.

      Returns:
      an array of character sets that are commonly used

    <!-- -->

    - #### getLocalCharacterSets

          public String[] getLocalCharacterSets(int platform)

      Returns the common Oracle character sets based on the language of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCharacterSet` method to find its translation.
      Note the common character sets vary among platforms.

      Parameters:
      `platform` - either `LocaleMapper.UNIX` or `LocaleMapper.WINDOWS` to specify the platform

      Returns:
      an array of character sets that are commonly used

    <!-- -->

    - #### getLocalCharacterSets

          public static String[] getLocalCharacterSets(String language)

      Returns the common Oracle character sets based on the given language. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCharacterSet` method to find its translation.
      Note the common character sets vary among platforms. This method returns the list for Unix platforms.

      Parameters:
      `language` - the Oracle language name

      Returns:
      an array of character sets that are commonly used

    <!-- -->

    - #### getLocalCharacterSets

          public static String[] getLocalCharacterSets(String language,
                                                       int platform)

      Returns the common Oracle character sets based on the given language. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCharacterSet` method to find its translation.
      Note the common character sets vary among platforms.

      Parameters:
      `language` - the Oracle language name

      `platform` - either `LocaleMapper.UNIX` or `LocaleMapper.WINDOWS` to specify the platform

      Returns:
      an array of character sets that are commonly used

    <!-- -->

    - #### getLocalCommonCharacterSets

          public static String[][] getLocalCommonCharacterSets(String language)

      Returns the common Oracle character sets based on the given language. The return strings are in English. Using the string, you can use OraDisplayLocaleInfo.getDisplayCharacterSet to find its translation.
      Note the common character sets vary among platforms. This method detects the platform and returns the corresponding list.

      Parameters:
      `language` - the Oracle language name

      Returns:
      a 2-dimensional array of character sets that are commonly used. The returned array has the structure of: {{ "primary charset", "common charset 2", "common charset 3", ... }, { "primary NCHAR charset", "common NCHAR charset 2", "common NCHAR charset 3", ... }} The first element is an array of common character set names. The first item in this array is the primary character set name, and remaining items are other common character set names. The number of items in this array is probably less than 20 (twenty). The second element is an array of common NCHAR character set names. The first item in this array is the primary NCHAR character set name, and remaining items are other common NCHAR character set names. The number of items in this array is probably only a few.

    <!-- -->

    - #### getLocalLinguisticSorts

          public static String[] getLocalLinguisticSorts(String language)

      Returns the common linguistic sorts based on the given language. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayLinguisticSort` method to find its translation.
      Parameters:
      `language` - the Oracle language name

      Returns:
      an array of linguistic sorting names that are commonly used

    <!-- -->

    - #### getLocalLinguisticSorts

          public String[] getLocalLinguisticSorts()

      Returns the common linguistic sorts based on the language of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayLinguisticSort` method to find its translation.
      Returns:
      an array of linguistic sorting names that are commonly used

    <!-- -->

    - #### getLocalCurrencies

          public static String[] getLocalCurrencies(String territory)

      Returns the common ISO 4217 currency codes based on the given territory. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCurrency` method to find its translation.
      Parameters:
      `territory` - the Oracle territory name

      Returns:
      ISO currency symbols

    <!-- -->

    - #### getLocalCurrencies

          public String[] getLocalCurrencies()

      Returns the common ISO 4217 currency based on the territory of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayCurrency` method to find its translation.
      Returns:
      ISO 4217 currency codes

    <!-- -->

    - #### getCurrencySymbol

          public static String getCurrencySymbol(String iso4217code)

      Returns the currency symbol based on the given ISO 4217 code.
      Parameters:
      `iso4217code` - ISO 4217 currency code

      Returns:
      a currency symbol

    <!-- -->

    - #### getCurrencySymbol

          public String getCurrencySymbol()

      Returns the currency symbol for this `OraLocaleInfo` instance.
      Returns:
      a currency symbol

    <!-- -->

    - #### getLocalTerritories

          public String[] getLocalTerritories()

      Returns the common Oracle territories based on the language of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayTerritory` mehtod to find its translation.
      Returns:
      an array of territories that are commonly used

    <!-- -->

    - #### getLocalTerritories

          public static String[] getLocalTerritories(String language)

      Returns the common Oracle territories based on the given language. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayTerritory` method to find its translation.
      Parameters:
      `language` - the Oracle language name

      Returns:
      an array of territories that are commonly used

    <!-- -->

    - #### getLocalLanguages

          public String[] getLocalLanguages()

      Returns the common Oracle languages based on the territory of this `OraLocaleInfo` instance. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayLanguage` method to find its translation.
      Returns:
      an array of languages that are commonly used

    <!-- -->

    - #### getLocalLanguages

          public static String[] getLocalLanguages(String territory)

      Returns the common Oracle languages based on the given territory. The return strings are in English. Using the string, you can use the `OraDisplayLocaleInfo.getDisplayLanguage` method to find its translation.
      Parameters:
      `territory` - the Oracle territory name

      Returns:
      an array of languages that are commonly used

    <!-- -->

    - #### getLocalTimeZones

          public static TimeZone[] getLocalTimeZones(String territory)

      Returns the common time zone list for the given Oracle territory.
      Parameters:
      `territory` - the Oracle territory name

      Returns:
      a common `TimeZone` object list

    <!-- -->

    - #### getLocalTimeZones

          public TimeZone[] getLocalTimeZones()

      Returns the common time zone list for the territory of this `OraLocaleInfo` instance.
      Returns:
      a common `TimeZone` object list

    <!-- -->

    - #### getAvailableLocale

          public static String[] getAvailableLocale()

      Returns the available Oracle locale list. Available locales are locales that are supported by the GDK.
      Returns:
      a list of Oracle locales in `<Oracle language>_<Oracle territory>` form

    <!-- -->

    - #### getCommonTimeZones

          public static TimeZone[] getCommonTimeZones()

      Returns the common time zone list. This is independent from locales.
      Returns:
      a common `TimeZone` object list

    <!-- -->

    - #### getCommonTimeZoneIDs

          public static String[] getCommonTimeZoneIDs()

      Returns the common time zone IDs in an array. This is independent from locales.
      Returns:
      a common time zone ID array

    <!-- -->

    - #### getCommonLocales

          public static Locale[] getCommonLocales()

      Returns the common locale list, i.e. locales that are commonly used. The common locale list is a subset of the "available" locales that the GDK supports.
      Returns:
      a common Java `Locale` object list

    <!-- -->

    - #### getCommonLocales

          public static Locale[] getCommonLocales(Locale translocale)

      Returns the common locale list that is sorted based on the given translation locale.
      Parameters:
      `translocale` - the translation locale

      Returns:
      a common Java `Locale` object list

    <!-- -->

    - #### getAvailableLanguages

          public static String[] getAvailableLanguages()

      Returns a list of the available Oracle languages, i.e. languages supported by the GDK.
      Returns:
      an array of Oracle language names

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

          public static String[] getAvailableTerritories()

      Returns a list of the available Oracle territories.
      Returns:
      an array of Oracle territory names

    <!-- -->

    - #### getAvailableTerritories

          public static String[][] getAvailableTerritories(Locale translocale)

      Returns the available territory IDs along with their corresponding display names sorted in the display name order.
      Parameters:
      `translocale` - the translation locale

      Returns:
      a sorted 2-dimensional array of available territories. The returned array has the structure of: {{ "territory ID 1", "territory ID 2", "territory ID 3", ... }, { "display name 1", "display name 2", "display name 3", ... }} The first element is an array of available territory IDs sorted based on the order of their translated display names. The second element is an array of the corresponding translated display names. In other words, for the returned array terr\[\]\[\], terr\[0\]\[i\] is a territory ID and terr\[1\]\[i\] contains its corresponding translated display name.

    <!-- -->

    - #### getAvailableCharacterSets

          public static String[] getAvailableCharacterSets()

      Returns a list of the available Oracle character sets.
      Returns:
      an array of Oracle character sets

    <!-- -->

    - #### getAvailableCurrencies

          public static String[] getAvailableCurrencies()

      Returns a list of the available ISO 4217 currencies.
      Returns:
      an array of ISO 4217 currencies

    <!-- -->

    - #### getAvailableLinguisticSorts

          public static String[] getAvailableLinguisticSorts()

      Returns a list of the available Oracle linguistic sorts.
      Returns:
      an array of Oracle linguistic sorts

    <!-- -->

    - #### getAvailableDBCharacterSets

          public static String[] getAvailableDBCharacterSets()

      Returns a list of the available database character set names depending on whether the platform is ascii-based or ebcdic-based.
      Returns:
      an array of valid database character sets based on the platform

    <!-- -->

    - #### getRecommendedDBCharacterSets

          public static String[] getRecommendedDBCharacterSets()

      Returns an alphabetically sorted list of the recommended database character set names depending on whether the platform is ASCII-based or EBCDIC-based.
      Returns:
      an alphabetically sorted array of recommended database character sets based on the platform

    <!-- -->

    - #### getAvailableNationalCharacterSets

          public static String[] getAvailableNationalCharacterSets()

      Returns a list of the available national character sets.
      Returns:
      an array of national character sets

    <!-- -->

    - #### getStartDayOfTheWeek

          public int getStartDayOfTheWeek()

      Returns the start day-of-the-week for the object. It is indicated by a number of 0 through 6.
      Returns:
      the start day-of-the-week

    <!-- -->

    - #### getStartDayOfTheWeek

          public static int getStartDayOfTheWeek(String territory)

      Returns the start day of the week for the given Oracle territory for the object. It is indicated by a number of 0 through 6.
      Parameters:
      `territory` - the Oracle territory name

      Returns:
      the start day of the week

    <!-- -->

    - #### getStartDayOfTheWeek

          public static int getStartDayOfTheWeek(String language,
                                                 String territory)

      Returns the start day of the week for the given Oracle language and Oracle territory for the object. It is indicated by a number of 0 through 6.
      Parameters:
      `language` - the Oracle language name

      `territory` - the Oracle territory name

      Returns:
      the start day of the week

    <!-- -->

    - #### clone

          public Object clone()

      Overrides the `clone` method.
      Overrides:
      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a copy of this `OraLocaleInfo` instance

      Throws:
      [`IllegalStateException`](http://docs.oracle.com/javase/8/docs/api/java/lang/IllegalStateException.html?is-external=true) - if the `OraCollator` object is invalid

    <!-- -->

    - #### equals

          public boolean equals(Object obj)

      Overrides the `equals` method.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `obj` - a target object to compare

      Returns:
      `true` if equal or `false` if not

    <!-- -->

    - #### getDefault

          public static OraLocaleInfo getDefault()

      Returns the default `OraLocaleInfo` instance based on the Oracle default locale.
      Returns:
      an `OraLocaleInfo` instance

    <!-- -->

    - #### toString

          public String toString()

      Returns the string representation of this `OraLocaleInfo` instance.
      Overrides:
      [`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a string

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides the `hashCode` method.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      a hash value

    <!-- -->

    - #### getLocaleFromString

          public static Locale getLocaleFromString(String localestring)

      Retrieves a Java `Locale` object that maps to the ISO locale string.
      Either a dash (U+002D) or an underscore (U+005F) can be used to connect ISO 639 and ISO 3166 codes.

      Parameters:
      `localestring` - the string representing an ISO locale. For example, `ja-JP` represents the Japanese language used in Japan. The connector of ISO 639 and ISO 3166 codes can be either "`-`" or "`_`".

      Returns:
      an Java `Locale` object

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

- [Prev Class](OraDisplayLocaleInfo.md)
- [Next Class](OraResourceBundle.md)

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
