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

- [Prev Class](ApplicationContext.md)
- [Next Class](ServletHelper.md)

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

## Class Localizer

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.Localizer

<!-- -->

-

  ------------------------------------------------------------------------



      public class Localizer
      extends Object

  The `Localizer` class is an all-in-one class that provides access to all necessary globalization services.
  The `Localizer` instance is derived from the [`ServletHelper.getLocalizerInstance(HttpServletRequest)`](ServletHelper.md) method that is associated with the current user locale. You may change the current locale on each page, therefore, the scope of `Localizer` is `page` scope.

  By using the `Localizer` class, you do not have to manually deal with the locale-sensitive operations. Instead, all information can be obtained from one `Localizer` object. The following functionalities of classes are included as part of Localizer's services:

  - `oracle.i18n.text.OraDateFormat`
  - `oracle.i18n.text.OraNumberFormat`
  - `oracle.i18n.text.OraCollator`
  - `oracle.i18n.util.OraLocaleInfo`
  - `oracle.i18n.util.LocaleMapper`

  Note: Strings returned by many `Localizer` methods, such as formatted dates and locale-specific currency symbols, depend on locale data that may be provided by users through URLs or form input. For example, the locale source class [`UserInput`](localesource/UserInput.md) provides various datetime format patterns and the ISO currency abbreviation retrieved from a page URL. A datetime format pattern may include double-quoted literal strings with arbitrary contents. To prevent cross-site script injection attacks, strings returned by `Localizer` methods must be properly escaped before being displayed as part of an HTML page, for example by applying the [`CharEntityReference.escape(String)`](../net/CharEntityReference.md) method.

  Since:
  10.1.0.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                   | Method and Description                                                                                                                                                                                                                                                                                                      |
    |-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                               | `compareString``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` target)`<br>Compares two strings using the current linguistic sort/collator object.                    |
    | `int`                                                                                               | `compareStringWithDefaultCollator``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` target)`<br>Compares two strings using the default linguistic sort/collator object. |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `decodeURL``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source)`<br>Decodes a URL string based on the current user character set using the character encoding of the page.                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `encodeURL``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` source)`<br>Encodes a URL string based on the current user character set using the character encoding of the page.                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatCurrency``(double nm)`<br>Formats a `double` value into a currency string.                                                                                                                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatCurrency``(long nm)`<br>Formats a `long` value into a currency string.                                                                                                                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatCurrency``(`[`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)` nm)`<br>Formats a `Number` object into a currency string.                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatDate``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` dt, int style)`<br>Formats a `Date` object into a text string representation of the date.                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatDateTime``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` dt, int datestyle)`<br>Formats a `Date` object into a text representation of the date and time.                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatNumber``(double nm)`<br>Formats a `double` value into a text representation of the number.                                                                                                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatNumber``(long nm)`<br>Formats a `long` value into a text representation of the number.                                                                                                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatNumber``(`[`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)` nm)`<br>Formats a `Number` object into a text representation of the number.                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `formatTime``(`[`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)` dt)`<br>Formats a `Date` object into its text representation of the time.                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getAlignment``(`[`LocaleSource.Alignment`](localesource/LocaleSource.Alignment.md)` alignment)`<br>Returns the current text alignment.                                                                                                                                                                                     |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getCurrencyPattern``()`<br>Returns the currency format pattern used.                                                                                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDatePattern``(int style)`<br>Returns the date format pattern used for the specified style.                                                                                                                                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDateTimePattern``(int datestyle)`<br>Returns the date and time format pattern used for the specified style.                                                                                                                                                                                                             |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayCharacterSet``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Returns a translated character set name.                                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayCountry``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated country/territory name.                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayCountry``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` country)`<br>Returns a translated country/territory name.                                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayCurrency``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` currencySymbol)`<br>Returns a translated currency name.                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayLanguage``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated language name.                                                                                                                                                         |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayLanguage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` language)`<br>Returns a translated language name.                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayLinguisticSort``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` linguisticSort)`<br>Returns a translated linguistic sorting name.                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns a translated locale name.                                                                                                                                                             |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayLocale``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraTerritory)`<br>Returns a translated locale name.                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayTerritory``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` territory)`<br>Returns a translated country/territory name.                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDisplayTimeZone``(`[`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)` tz)`<br>Returns a translated time zone name.                                                                                                                                                        |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getIANACharacterSet``()`<br>Returns the IANA character set name used for the client.                                                                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getIANAPageCharacterSet``()`<br>Returns the character set encoding of the page.                                                                                                                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getISOCurrency``()`<br>Returns the ISO 4217 currency code for the country of the current locale.                                                                                                                                                                                                                           |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)         | `getLocale``()`<br>Returns the `Locale` object representing the current locale.                                                                                                                                                                                                                                             |
    | [`Class`](http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)`[]`       | `getLocaleSources``()`<br>Returns locale sources examined in this order to determine the current locale.                                                                                                                                                                                                                    |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalIANACharacterSets``()`<br>Returns an array of local character sets for the current language.                                                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalLinguisticSorts``()`<br>Returns an array of local Oracle linguistic sort names for the current language.                                                                                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalOraLanguages``()`<br>Returns an array of local languages for the current territory.                                                                                                                                                                                                                                |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getLocalOraTerritories``()`<br>Returns an array of local territories for the current language.                                                                                                                                                                                                                             |
    | [`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)`[]` | `getLocalTimeZones``()`<br>Returns an array of local `TimeZone` objects for the current territory.                                                                                                                                                                                                                          |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getMessage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key)`<br>Returns a localized message associated with the key for the current locale.                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getMessage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key, `[`Class`](http://docs.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` base)`<br>Returns a localized message associated with the key for the current locale.                          |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getMessage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` key, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` baseKeyName)`<br>Returns a localized message associated with the key for the current locale.                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getNumberPattern``()`<br>Returns the number format pattern used.                                                                                                                                                                                                                                                           |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getOraCharacterSet``()`<br>Returns the Oracle character set name used for the client and decoding URLs.                                                                                                                                                                                                                    |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getOraLanguage``()`<br>Returns the Oracle language name.                                                                                                                                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getOraShortLanguage``()`<br>Returns the short form of the Oracle language name.                                                                                                                                                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getOraTerritory``()`<br>Returns the Oracle territory name.                                                                                                                                                                                                                                                                 |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getParameterName``(`[`LocaleSource.Parameter`](localesource/LocaleSource.Parameter.md)` parameter)`<br>Returns a `String` representing the parameter name used to specify locale attributes.                                                                                                                               |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getSupportedIANACharacterSets``()`<br>Returns supported IANA character sets.                                                                                                                                                                                                                                               |
    | [`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)`[]`     | `getSupportedLocales``()`<br>Returns locales supported in the application.                                                                                                                                                                                                                                                  |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getSupportedOraLanguages``()`<br>Returns supported Oracle languages.                                                                                                                                                                                                                                                       |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getSupportedOraLanguages``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraTerritory)`<br>Returns supported Oracle languages for the given Oracle territory.                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getSupportedOraTerritories``()`<br>Returns supported Oracle territories.                                                                                                                                                                                                                                                   |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`     | `getSupportedOraTerritories``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage)`<br>Returns supported Oracle territories for the given Oracle language.                                                                                                            |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getTimePattern``()`<br>Returns the time format pattern.                                                                                                                                                                                                                                                                    |
    | [`TimeZone`](http://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html?is-external=true)     | `getTimeZone``()`<br>Returns the current `TimeZone` object.                                                                                                                                                                                                                                                                 |
    | [`LocaleSource.WritingDirection`](localesource/LocaleSource.WritingDirection.md)                    | `getWritingDirection``()`<br>Returns the current text display writing direction.                                                                                                                                                                                                                                            |
    | [`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)         | `parseCurrency``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Parses a text representation of the currency amount into `Number` object.                                                                                                                           |
    | [`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)             | `parseDate``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, int style)`<br>Parses a text representation of the date into a `Date` object.                                                                                                                               |
    | [`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)             | `parseDateTime``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, int datestyle)`<br>Parses a text representation of the date and time into a `Date` object.                                                                                                              |
    | [`Number`](http://docs.oracle.com/javase/8/docs/api/java/lang/Number.html?is-external=true)         | `parseNumber``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Parses a text representation of the number into a `Number` object.                                                                                                                                    |
    | [`Date`](http://docs.oracle.com/javase/8/docs/api/java/util/Date.html?is-external=true)             | `parseTime``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Parses a text representation of the time into a `Date` object.                                                                                                                                          |
    | `boolean`                                                                                           | `synchronizeLocale``(`[`Connection`](http://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` con)`<br>Synchronizes the NLS parameters of the database session with this object.                                                                                                                |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Method Detail

    - #### getLocale

          public Locale getLocale()

      Returns the `Locale` object representing the current locale.
      The same value is returned by the `HttpServletRequest.getLocale` method in JSP/Java Servlet application code.

      Returns:
      a `Locale` object

    <!-- -->

    - #### getOraLanguage

          public String getOraLanguage()

      Returns the Oracle language name.
      Returns:
      a `String` representing the Oracle language name

    <!-- -->

    - #### getOraTerritory

          public String getOraTerritory()

      Returns the Oracle territory name.
      Returns:
      a `String` representing the Oracle territory name

    <!-- -->

    - #### getOraCharacterSet

          public String getOraCharacterSet()

      Returns the Oracle character set name used for the client and decoding URLs.
      Returns:
      a `String` representing the Oracle character set name

    <!-- -->

    - #### getOraShortLanguage

          public String getOraShortLanguage()

      Returns the short form of the Oracle language name.
      Returns:
      a `String` representing the short form of the Oracle language name

    <!-- -->

    - #### getTimeZone

          public TimeZone getTimeZone()

      Returns the current `TimeZone` object.
      If the `TimeZone` object is not set for the current user, returns the default `TimeZone` object for the user locale.

      Returns:
      a `TimeZone` object

    <!-- -->

    - #### getWritingDirection

          public LocaleSource.WritingDirection getWritingDirection()

      Returns the current text display writing direction.
      The returned `LocaleSource.WritingDirection` value is used as follows:

           <%
             Localizer localizer = ServletHelper.getLocalizerInstance(request);
           %>
           <table dir="<%=localizer.getWritingDirection()%>"
           ... >
           ...
           </table>


      Returns:
      the `LocaleSource.WritingDirection` object

    <!-- -->

    - #### getAlignment

          public String getAlignment(LocaleSource.Alignment alignment)

      Returns the current text alignment.
      For example, if LTR mode, the `"Text Data"` is aligned to the `right`, otherwise the `left`.

           <%
             Localizer localizer = ServletHelper.getLocalizerInstance(request);
           %>
           <table ... >
           <tr>
           <td align="<%=localizer.getAlignment(LocaleSource.Alignment.END)%>">
           Text Data</td></tr>
           ...
           </table>


      Parameters:
      `alignment` - `LocaleSource.Alignment.START` or `LocaleSource.Alignment.END`

      Returns:
      `String` object either `"left"` or `"right"`

    <!-- -->

    - #### getISOCurrency

          public String getISOCurrency()

      Returns the ISO 4217 currency code for the country of the current locale.
      Returns:
      ISO 4217 currency code

    <!-- -->

    - #### getIANACharacterSet

          public String getIANACharacterSet()

      Returns the IANA character set name used for the client.
      Returns:
      IANA character set name

    <!-- -->

    - #### formatDate

          public String formatDate(Date dt,
                                   int style)

      Formats a `Date` object into a text string representation of the date. The required text format is specified by method arguments.
      Parameters:
      `dt` - `java.util.Date` object to format

      `style` - format of text data; either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`

      Returns:
      `String` representing the date

    <!-- -->

    - #### parseDate

          public Date parseDate(String str,
                                int style)
                         throws ParseException

      Parses a text representation of the date into a `Date` object.
      Parameters:
      `str` - `String` be parsed

      `style` - format of text data, either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`

      Returns:
      `Date` parsed from the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the specified string cannot be parsed

    <!-- -->

    - #### getDatePattern

          public String getDatePattern(int style)

      Returns the date format pattern used for the specified style.
      Parameters:
      `style` - a pattern style, either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`

      Returns:
      the format pattern

    <!-- -->

    - #### formatTime

          public String formatTime(Date dt)

      Formats a `Date` object into its text representation of the time.
      Parameters:
      `dt` - `java.util.Date` object to format

      Returns:
      `String` representing the time

    <!-- -->

    - #### parseTime

          public Date parseTime(String str)
                         throws ParseException

      Parses a text representation of the time into a `Date` object.
      Parameters:
      `str` - `String` to be parsed

      Returns:
      `Date` parsed from the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the specified string cannot be parsed

    <!-- -->

    - #### getTimePattern

          public String getTimePattern()

      Returns the time format pattern.
      Returns:
      the format pattern

    <!-- -->

    - #### formatDateTime

          public String formatDateTime(Date dt,
                                       int datestyle)

      Formats a `Date` object into a text representation of the date and time. The required text format is specified by the style argument.
      Parameters:
      `dt` - `java.util.Date` object to format

      `datestyle` - format of text data for the date, either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`. The time element does not have a style.

      Returns:
      `String` representing the date and time

    <!-- -->

    - #### parseDateTime

          public Date parseDateTime(String str,
                                    int datestyle)
                             throws ParseException

      Parses a text representation of the date and time into a `Date` object. The passed in style of the date/time string is used for the proper parsing of the string.
      Parameters:
      `str` - `String` to be parsed

      `datestyle` - format of text data for the date, either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`. The time element does not have a style.

      Returns:
      `Date` parsed from the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the specified string cannot be parsed

    <!-- -->

    - #### getDateTimePattern

          public String getDateTimePattern(int datestyle)

      Returns the date and time format pattern used for the specified style.
      You cannot specify the style of time.

      Parameters:
      `datestyle` - format of text data, either `OraDateFormat.LONG`, `OraDateFormat.SHORT`, or `OraDateFormat.DEFAULT`

      Returns:
      the format pattern

    <!-- -->

    - #### formatNumber

          public String formatNumber(Number nm)

      Formats a `Number` object into a text representation of the number.
      Parameters:
      `nm` - `Number` object to format

      Returns:
      `String` representing the number

    <!-- -->

    - #### parseNumber

          public Number parseNumber(String str)
                             throws ParseException

      Parses a text representation of the number into a `Number` object.
      Parameters:
      `str` - `String` be parsed

      Returns:
      `Number` parsed from the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the specified string cannot be parsed

    <!-- -->

    - #### getNumberPattern

          public String getNumberPattern()

      Returns the number format pattern used.
      Returns:
      the format pattern

    <!-- -->

    - #### formatNumber

          public String formatNumber(double nm)

      Formats a `double` value into a text representation of the number.
      Parameters:
      `nm` - `double` value to format

      Returns:
      `String` representing the number

    <!-- -->

    - #### formatNumber

          public String formatNumber(long nm)

      Formats a `long` value into a text representation of the number.
      Parameters:
      `nm` - `long` value to format

      Returns:
      `String` representing the number

    <!-- -->

    - #### formatCurrency

          public String formatCurrency(Number nm)

      Formats a `Number` object into a currency string.
      Parameters:
      `nm` - `Number` object to format

      Returns:
      `String` representing the currency amount

    <!-- -->

    - #### parseCurrency

          public Number parseCurrency(String str)
                               throws ParseException

      Parses a text representation of the currency amount into `Number` object.
      Parameters:
      `str` - `String` be parsed

      Returns:
      `Number` parsed from the string

      Throws:
      [`ParseException`](http://docs.oracle.com/javase/8/docs/api/java/text/ParseException.html?is-external=true) - if the specified string cannot be parsed

    <!-- -->

    - #### getCurrencyPattern

          public String getCurrencyPattern()

      Returns the currency format pattern used.
      Returns:
      the format pattern

    <!-- -->

    - #### formatCurrency

          public String formatCurrency(double nm)

      Formats a `double` value into a currency string.
      Parameters:
      `nm` - `double` value to format

      Returns:
      `String` representing the currency amount

    <!-- -->

    - #### formatCurrency

          public String formatCurrency(long nm)

      Formats a `long` value into a currency string.
      Parameters:
      `nm` - `long` value to format

      Returns:
      `String` representing the currency amount

    <!-- -->

    - #### compareString

          public int compareString(String source,
                                   String target)

      Compares two strings using the current linguistic sort/collator object.
      Parameters:
      `source` - the source string to be compared

      `target` - the target string to be compared

      Returns:
      `OraCollator.EQUAL` if source collation values equal the target values, or
      `OraCollator.LESS` if source collation values are smaller than target values, or
      `OraCollator.GREATER` if source collation values are larger than target values

    <!-- -->

    - #### compareStringWithDefaultCollator

          public int compareStringWithDefaultCollator(String source,
                                                      String target)

      Compares two strings using the default linguistic sort/collator object.
      This method is provided for the compatible operations.

      Parameters:
      `source` - the source string to be compared

      `target` - the target string to be compared

      Returns:
      `OraCollator.EQUAL` if source collation values equal the target values, or
      `OraCollator.LESS` if source collation values are smaller than target values, or
      `OraCollator.GREATER` if source collation values are larger than target values

    <!-- -->

    - #### getMessage

          public String getMessage(String key,
                                   Class base)

      Returns a localized message associated with the key for the current locale.
      Parameters:
      `key` - a key string

      `base` - a base class name of the message resource bundle

      Returns:
      a localized message

    <!-- -->

    - #### getMessage

          public String getMessage(String key,
                                   String baseKeyName)

      Returns a localized message associated with the key for the current locale.
      Parameters:
      `key` - a key string

      `baseKeyName` - a base key class name of the message resource bundle

      Returns:
      a localized message

    <!-- -->

    - #### getMessage

          public String getMessage(String key)

      Returns a localized message associated with the key for the current locale.
      Parameters:
      `key` - a key string

      Returns:
      a localized message

    <!-- -->

    - #### getLocalOraLanguages

          public String[] getLocalOraLanguages()

      Returns an array of local languages for the current territory.
      Returns:
      an array of Oracle languages

    <!-- -->

    - #### getLocalOraTerritories

          public String[] getLocalOraTerritories()

      Returns an array of local territories for the current language.
      Returns:
      an array of Oracle territories

    <!-- -->

    - #### getLocalIANACharacterSets

          public String[] getLocalIANACharacterSets()

      Returns an array of local character sets for the current language.
      Returns:
      an array of IANA territories

    <!-- -->

    - #### getLocalTimeZones

          public TimeZone[] getLocalTimeZones()

      Returns an array of local `TimeZone` objects for the current territory.
      Returns:
      an array of Java `TimeZone` objects

    <!-- -->

    - #### getLocalLinguisticSorts

          public String[] getLocalLinguisticSorts()

      Returns an array of local Oracle linguistic sort names for the current language.
      Returns:
      an array of `String` containing Oracle linguistic sort names

    <!-- -->

    - #### getDisplayLocale

          public String getDisplayLocale(Locale locale)

      Returns a translated locale name.
      Parameters:
      `locale` - a locale to be translated

      Returns:
      a translated string

    <!-- -->

    - #### getDisplayLocale

          public String getDisplayLocale(String oraLanguage,
                                         String oraTerritory)

      Returns a translated locale name.
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
      `language` - a language name

      Returns:
      a translated language name

    <!-- -->

    - #### getDisplayCountry

          public String getDisplayCountry(Locale locale)

      Returns a translated country/territory name.
      Parameters:
      `locale` - a locale that includes the country to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayCountry

          public String getDisplayCountry(String country)

      Returns a translated country/territory name.
      Parameters:
      `country` - a country name to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayTerritory

          public String getDisplayTerritory(String territory)

      Returns a translated country/territory name.
      Parameters:
      `territory` - a country name to be translated

      Returns:
      a translated country name

    <!-- -->

    - #### getDisplayTimeZone

          public String getDisplayTimeZone(TimeZone tz)

      Returns a translated time zone name.
      If the translation is not found, the return value is composed using `getRawOffset()` value in the form of `(SHH:MM)` where `S` for a sign of the value, `HH` represents the hours of the offset, and `MM` represents the minutes of the offset.

      Parameters:
      `tz` - a time zone to be translated

      Returns:
      a translated time zone name

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
      `charset` - a character set name to be translated

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

    - #### encodeURL

          public String encodeURL(String source)

      Encodes a URL string based on the current user character set using the character encoding of the page.
      Parameters:
      `source` - a source string to encode

      Returns:
      an encoded string

    <!-- -->

    - #### decodeURL

          public String decodeURL(String source)

      Decodes a URL string based on the current user character set using the character encoding of the page.
      Parameters:
      `source` - a source string to decode

      Returns:
      a decoded string

    <!-- -->

    - #### synchronizeLocale

          public boolean synchronizeLocale(Connection con)
                                    throws SQLException

      Synchronizes the NLS parameters of the database session with this object.
      This executes `ALTER SESSION` SQL commands to set NLS session parameters to synchronize the locale and attributes in this object. The following session parameters are updated:

      - `NLS_LANGUAGE`
      - `NLS_TERRITORY`
      - `NLS_DATE_LANGUAGE`
      - `NLS_DATE_FORMAT`
      - `NLS_CURRENCY`
      - `NLS_ISO_CURRENCY`
      - `NLS_COMP`
      - `NLS_SORT`

      Note: Other threads can override NLS session parameters with different values while your thread is active. For this reason, this method is not suitable for a multilingual application that handles multiple locales in a single instance. Instead, develop applications that are as independent from NLS session parameters as possible.
      Parameters:
      `con` - the connection object for the database. Make sure the connection is established, othewise you will get an `SQLException` error.

      Returns:
      `true` if the SQL execution is successfull, otherwise `false`

      Throws:
      [`SQLException`](http://docs.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getParameterName

          public String getParameterName(LocaleSource.Parameter parameter)

      Returns a `String` representing the parameter name used to specify locale attributes. For example, if you want to get the locale value, use the `LocaleSource.LOCALE` object as an input:
           ApplicationContext appctx = ServletHelper.getApplicationContextInstance(
             request);
           String locale = request.getParameter(
             appctx.getParameterName(LocaleSource.LOCALE));


      Parameters:
      `parameter` - a parameter type

      Returns:
      a parameter name used in the application

    <!-- -->

    - #### getSupportedLocales

          public Locale[] getSupportedLocales()

      Returns locales supported in the application.
      The supported locale can be specified in the application configuration file.

      Returns:
      an array of `Locale` objects representing supported locales in the application

    <!-- -->

    - #### getIANAPageCharacterSet

          public String getIANAPageCharacterSet()

      Returns the character set encoding of the page.
      Returns:
      an IANA character set name

    <!-- -->

    - #### getLocaleSources

          public Class[] getLocaleSources()

      Returns locale sources examined in this order to determine the current locale.
      Returns:
      an array of `LocaleSource` classes

    <!-- -->

    - #### getSupportedOraLanguages

          public String[] getSupportedOraLanguages(String oraTerritory)

      Returns supported Oracle languages for the given Oracle territory.
      The supported languages are determined by the supported locale. Sorting order is in the English language.

      Parameters:
      `oraTerritory` - Oracle territory name

      Returns:
      an array of `String` representing the supported languages in the application

    <!-- -->

    - #### getSupportedOraLanguages

          public String[] getSupportedOraLanguages()

      Returns supported Oracle languages.
      The supported languages are determined by the supported locale. Sorting order is in the English language.

      Returns:
      an array of `String` representing the supported languages in the application

    <!-- -->

    - #### getSupportedOraTerritories

          public String[] getSupportedOraTerritories(String oraLanguage)

      Returns supported Oracle territories for the given Oracle language.
      The supported territories are determined by the supported locale. Sorting order is in the English language.

      Parameters:
      `oraLanguage` - Oracle langauge name

      Returns:
      an array of `String` representing the supported territories in the application

    <!-- -->

    - #### getSupportedOraTerritories

          public String[] getSupportedOraTerritories()

      Returns supported Oracle territories.
      The supported territories are determined by the supported locale. Sorting order is in the English language.

      Returns:
      an array of `String` representing the supported territories in the application

    <!-- -->

    - #### getSupportedIANACharacterSets

          public String[] getSupportedIANACharacterSets()

      Returns supported IANA character sets.
      Returns:
      an array of supported IANA character sets in the application

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

- [Prev Class](ApplicationContext.md)
- [Next Class](ServletHelper.md)

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
