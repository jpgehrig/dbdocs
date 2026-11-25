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

- [Prev Class](DualInputStreamBuilder.md)
- [Next Class](OraDisplayLocaleInfo.md)

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

## Class LocaleMapper

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.util.LocaleMapper

<!-- -->

-

  ------------------------------------------------------------------------



      public class LocaleMapper
      extends Object

  The `LocaleMapper` class maps between Oracle locale elements and equivalent locale elements in other vendors and standards. This class contains the same mapping data as the NLSRTL C library and Java `oracle.gss.util` package.
  The locale mappings are available for Oracle and Java locales. The character set encoding mappings are available for Oracle, Java, and IANA.

  Oracle character set encoding is the character set part of the `NLS_LANG` parameter. Java character set encoding is the available character set in Java. IANA character set encoding is the character set that is defined by IANA and widely used by various applications such as web browser or e-mail application.

  Since:
  10.1.0.2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                              |
    |-------------------|--------------------------------------------------------------------|
    | `static int`      | `EMAIL_UNIX`<br>Constant value to represent Unix for e-mail.       |
    | `static int`      | `EMAIL_WINDOWS`<br>Constant value to represent Windows for e-mail. |
    | `static int`      | `IANA`<br>Constant value to represent IANA.                        |
    | `static int`      | `JAVA`<br>Constant value to represent Java.                        |
    | `static int`      | `ORACLE`<br>Constant value to represent Oracle.                    |
    | `static int`      | `UNIX`<br>Constant value to represent Unix in general.             |
    | `static int`      | `WINDOWS`<br>Constant value to represent Windows in general.       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                         |
    |----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getAvailableIANACharacterSets``()`<br>Returns an array of all IANA character set names that have corresponding Oracle character sets.                                                                                                                                                                                                                                         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getAvailableOraCharacterSets``()`<br>Returns an array of all Oracle character set names that have corresponding IANA character sets.                                                                                                                                                                                                                                          |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getIANACharacterSet``(int from, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Returns the IANA character set that is equivalent to the passed in Oracle or Java character set.                                                                                                                                   |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getIANACharSetFromLocale``(int context, `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the commonly used IANA character set based on the given context and locale.                                                                                                                                         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getIANACharSetFromOraLang``(int context, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage)`<br>Returns the commonly used IANA character set based on the given context and Oracle language.                                                                                                                          |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getJavaCharacterSet``(int from, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Returns the Java character set that is equivalent to the passed in Oracle or IANA character set.                                                                                                                                   |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getJavaLangFromOraLang``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns the ISO 639 two-letter code for the given Oracle language name.                                                                                                                                                                      |
    | `static `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)     | `getJavaLocale``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` nlsLocale)`<br>Returns a Java `Locale` instance that is equivalent to the Oracle locale specified by the passed in Oracle language and territory.                                                                                                               |
    | `static `[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)     | `getJavaLocale``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraTerritory)`<br>Returns a Java `Locale` instance that is equivalent to the Oracle locale specified by the passed in Oracle language and territory. |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getJavaTerrFromOraTerr``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` terr)`<br>Returns the ISO 3166 two-letter code for the given Oracle territory name.                                                                                                                                                                    |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraCharacterSet``(int from, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset)`<br>Returns the Oracle character set that is equivalent to the passed in Java character set.                                                                                                                                            |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]` | `getOraCharSetFromOraLang``(int context, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage)`<br>Returns the commonly used Oracle character set based on the given context and Oracle language.                                                                                                                         |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraLangFromJavaLang``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` lang)`<br>Returns the Oracle language name for the given ISO 639 two-letter code.                                                                                                                                                                      |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraLanguage``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the Oracle language name based on the given Java `Locale` instance.                                                                                                                                                                        |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraLanguageFromShortName``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraShortName)`<br>Returns the Oracle language name from the Oracle short language name.                                                                                                                                                           |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraLinguisticSortFromLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the default Oracle linguistic sort name for the locale.                                                                                                                                                                    |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraLocale``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the Oracle language and Oracle territory name for the given Java `Locale` instance in the `<Oracle Language>_<Oracle Territory>` form.                                                                                                       |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraShortNameFromLanguage``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` oraLanguage)`<br>Returns the Oracle short language name from the Oracle language name.                                                                                                                                                            |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraTerrFromJavaTerr``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` terr)`<br>Returns the Oracle territory name for the given ISO 3166 two-letter code.                                                                                                                                                                    |
    | `static `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)     | `getOraTerritory``(`[`Locale`](http://docs.oracle.com/javase/8/docs/api/java/util/Locale.html?is-external=true)` locale)`<br>Returns the Oracle territory name for the given Java `Locale` instance.                                                                                                                                                                           |
    | `static boolean`                                                                                         | `isSupersetOf``(int csid, int key)`<br>Return true if the charset ID specified by key is a superset of the charset specified by csid                                                                                                                                                                                                                                           |
    | `static void`                                                                                            | `setJavaCharacterSet``(int from, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` charset, `[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` encoding)`<br>Associates a default encoding with a character set.                                                                        |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### ORACLE

          public static final int ORACLE

      Constant value to represent Oracle.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IANA

          public static final int IANA

      Constant value to represent IANA.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JAVA

          public static final int JAVA

      Constant value to represent Java.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EMAIL_WINDOWS

          public static final int EMAIL_WINDOWS

      Constant value to represent Windows for e-mail.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EMAIL_UNIX

          public static final int EMAIL_UNIX

      Constant value to represent Unix for e-mail.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WINDOWS

          public static final int WINDOWS

      Constant value to represent Windows in general.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UNIX

          public static final int UNIX

      Constant value to represent Unix in general.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getAvailableIANACharacterSets

          public static String[] getAvailableIANACharacterSets()

      Returns an array of all IANA character set names that have corresponding Oracle character sets.
      Returns:
      an array of `String` containing the list of IANA names

    <!-- -->

    - #### getAvailableOraCharacterSets

          public static String[] getAvailableOraCharacterSets()

      Returns an array of all Oracle character set names that have corresponding IANA character sets.
      Returns:
      an array of `String` containing the list of Oracle names

    <!-- -->

    - #### isSupersetOf

          public static boolean isSupersetOf(int csid,
                                             int key)

      Return true if the charset ID specified by key is a superset of the charset specified by csid

    <!-- -->

    - #### getIANACharacterSet

          public static String getIANACharacterSet(int from,
                                                   String charset)

      Returns the IANA character set that is equivalent to the passed in Oracle or Java character set.
      Parameters:
      `from` - can be `ORACLE` or `JAVA`

      `charset` - character set name with which we want to find an equivalent IANA character set

      Returns:
      IANA character set name, `null` if not found

    <!-- -->

    - #### setJavaCharacterSet

          public static void setJavaCharacterSet(int from,
                                                 String charset,
                                                 String encoding)
                                          throws UnsupportedEncodingException

      Associates a default encoding with a character set. This method can be used to choose a default encoding associated with a character set that can be represented as various flavors of encodings. Once the default encoding is associated, any calls to the `LocaleMapper.getJavaCharacterSet(int, String)` method will retrieve the associated encoding. For instance:

             LocaleMapper.setJavaCharacterSet(LocaleMapper.IANA,
                                       "ISO-2022-JP", "X-ORACLE-ISO2022-JP-OUTLOOK");
             ...

             // cs will be assigned the value "X-ORACLE-ISO2022-JP-OUTLOOK"
             String cs = LocaleMapper.getJavaCharacterSet(IANA, "ISO-2022-JP");



      Parameters:
      `from` - - must be IANA (for now)

      `charset` - - IANA charset name

      `encoding` - - the encoding to which we want to set

      Throws:
      [`UnsupportedEncodingException`](http://docs.oracle.com/javase/8/docs/api/java/io/UnsupportedEncodingException.html?is-external=true)

    <!-- -->

    - #### getJavaCharacterSet

          public static String getJavaCharacterSet(int from,
                                                   String charset)

      Returns the Java character set that is equivalent to the passed in Oracle or IANA character set.
      Parameters:
      `from` - can be `ORACLE` or `IANA`

      `charset` - character set name with which we want to find an equivalent Java character set

      Returns:
      Java character set name, `null` if not found

    <!-- -->

    - #### getOraCharacterSet

          public static String getOraCharacterSet(int from,
                                                  String charset)

      Returns the Oracle character set that is equivalent to the passed in Java character set.
      Parameters:
      `from` - can be `IANA` or `JAVA`

      `charset` - character set name with which we want to find an equivalent Oracle character set

      Returns:
      Oracle character set name, `null` if not found

    <!-- -->

    - #### getJavaLocale

          public static Locale getJavaLocale(String nlsLocale)

      Returns a Java `Locale` instance that is equivalent to the Oracle locale specified by the passed in Oracle language and territory.
      Parameters:
      `nlsLocale` - `NLS_LANG` string where Oracle language and territory are connected with the underscore '\_'

      Returns:
      Java `Locale` instance; defaults to `en_US`

    <!-- -->

    - #### getJavaLocale

          public static Locale getJavaLocale(String oraLanguage,
                                             String oraTerritory)

      Returns a Java `Locale` instance that is equivalent to the Oracle locale specified by the passed in Oracle language and territory.
      Parameters:
      `oraLanguage` - Oracle language

      `oraTerritory` - Oracle territory

      Returns:
      Java `Locale` instance; defaults to `en_US`

    <!-- -->

    - #### getOraLanguageFromShortName

          public static String getOraLanguageFromShortName(String oraShortName)

      Returns the Oracle language name from the Oracle short language name.
      Parameters:
      `oraShortName` - Oracle short language name

      Returns:
      Oracle language name

    <!-- -->

    - #### getOraShortNameFromLanguage

          public static String getOraShortNameFromLanguage(String oraLanguage)

      Returns the Oracle short language name from the Oracle language name.
      Parameters:
      `oraLanguage` - Oracle language name

      Returns:
      Oracle short language name

    <!-- -->

    - #### getOraLanguage

          public static String getOraLanguage(Locale locale)

      Returns the Oracle language name based on the given Java `Locale` instance.
      Parameters:
      `locale` - Java `Locale` instance

      Returns:
      Oracle language name associated with the given locale, or `null` if no corresponding Oracle language is found

    <!-- -->

    - #### getOraTerritory

          public static String getOraTerritory(Locale locale)

      Returns the Oracle territory name for the given Java `Locale` instance.
      Parameters:
      `locale` - Java `Locale` instance

      Returns:
      Oracle territory name associated with the given Java `Locale` instance

    <!-- -->

    - #### getOraLocale

          public static String getOraLocale(Locale locale)

      Returns the Oracle language and Oracle territory name for the given Java `Locale` instance in the `<Oracle Language>_<Oracle Territory>` form.
      Parameters:
      `locale` - a Java `Locale` instance

      Returns:
      Oracle language and territory name associated with the given Java `Locale` instance

    <!-- -->

    - #### getIANACharSetFromLocale

          public static String[] getIANACharSetFromLocale(int context,
                                                          Locale locale)

      Returns the commonly used IANA character set based on the given context and locale. For example, an e-mail application may need to use a different character set than a web application.
      Parameters:
      `context` - can be `EMAIL_WINDOWS`, `EMAIL_UNIX`, `WINDOWS`, or `UNIX`

      `locale` - Java `Locale` instance

      Returns:
      IANA character set name for the given Java `Locale` instance

    <!-- -->

    - #### getIANACharSetFromOraLang

          public static String[] getIANACharSetFromOraLang(int context,
                                                           String oraLanguage)

      Returns the commonly used IANA character set based on the given context and Oracle language. For example, an e-mail application may need to use a different character set than a web application.
      Parameters:
      `context` - can be `EMAIL_WINDOWS`, `EMAIL_UNIX`, `WINDOWS`, or `UNIX`

      `oraLanguage` - Oracle language

      Returns:
      IANA character set name for the given Oracle language, if the language is null, then return null

    <!-- -->

    - #### getOraCharSetFromOraLang

          public static String[] getOraCharSetFromOraLang(int context,
                                                          String oraLanguage)

      Returns the commonly used Oracle character set based on the given context and Oracle language. For example, an e-mail application may need to use a different character set than a web application.
      Parameters:
      `context` - can be `EMAIL_WINDOWS`, `EMAIL_UNIX`, `WINDOWS`, or `UNIX`

      `oraLanguage` - Oracle language

      Returns:
      Oracle character set name for the given Oracle language

    <!-- -->

    - #### getOraLinguisticSortFromLocale

          public static String getOraLinguisticSortFromLocale(Locale locale)

      Returns the default Oracle linguistic sort name for the locale.
      Parameters:
      `locale` - the locale

      Returns:
      the default linguistic sort name

    <!-- -->

    - #### getOraLangFromJavaLang

          public static String getOraLangFromJavaLang(String lang)

      Returns the Oracle language name for the given ISO 639 two-letter code.
      Due to the limitation that uses the same ISO 639 two-letter code, `zh` for Simplified Chinese and Traditional Chinese, the two languages cannot be distinguished. In fact, if `zh` is given, this method returns Simplified Chinese only; it never returns Traditional Chinese.
      Use the `LocaleMapper.getOraLanguage(java.util.Locale)` method if those two Chinese languages need to be distinguished.

      Parameters:
      `lang` - ISO 639 two-letter code

      Returns:
      Oracle language name

    <!-- -->

    - #### getJavaLangFromOraLang

          public static String getJavaLangFromOraLang(String lang)

      Returns the ISO 639 two-letter code for the given Oracle language name.
      Due to the same reason discussed in the `LocaleMapper.getOraLangFromJavaLang(java.lang.String)` method, if either Simplified Chinese or Traditional Chinese is specified, this method always returns `zh`, which means loss of information.
      Use the `LocaleMapper.getJavaLocale(java.lang.String)` method instead.

      Parameters:
      `lang` - Oracle language name

      Returns:
      ISO 639 two-letter code

    <!-- -->

    - #### getOraTerrFromJavaTerr

          public static String getOraTerrFromJavaTerr(String terr)

      Returns the Oracle territory name for the given ISO 3166 two-letter code.
      Parameters:
      `terr` - ISO 3166 two-letter code

      Returns:
      Oracle territory name

    <!-- -->

    - #### getJavaTerrFromOraTerr

          public static String getJavaTerrFromOraTerr(String terr)

      Returns the ISO 3166 two-letter code for the given Oracle territory name.
      Parameters:
      `terr` - Oracle territory name

      Returns:
      ISO 3166 two-letter code

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

- [Prev Class](DualInputStreamBuilder.md)
- [Next Class](OraDisplayLocaleInfo.md)

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
