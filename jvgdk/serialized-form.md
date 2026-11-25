Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package oracle.i18n.net

  - ### Class oracle.i18n.net.OraInternetAddress extends [InternetAddress](http://docs.oracle.com/javaee/7/api/javax/mail/internet/InternetAddress.html?is-external=true) implements Serializable

- ## Package oracle.i18n.servlet.localesource

  - ### Class [oracle.i18n.servlet.localesource.ApplicationDefault](oracle/i18n/servlet/localesource/ApplicationDefault.md) extends [LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) implements Serializable

  - ### Class [oracle.i18n.servlet.localesource.DBLocaleSource](oracle/i18n/servlet/localesource/DBLocaleSource.md) extends [LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) implements Serializable

    - ### Serialized Fields

      - #### m_user

            String m_user

      - #### m_appctx

            ApplicationContext m_appctx

      - #### m_params

            Map m_params

      - #### m_datasrc

            DataSource m_datasrc

      - #### m_servletContext

            ServletContext m_servletContext

      - #### m_diagnosticsLevel

            int m_diagnosticsLevel

      - #### m_is_locale

            boolean m_is_locale

      - #### m_is_short_lang

            boolean m_is_short_lang

      - #### m_loadStatement

            String m_loadStatement

      - #### m_storeStatement

            String m_storeStatement

      - #### m_paramList

            List m_paramList

  - ### Class [oracle.i18n.servlet.localesource.HttpAcceptLanguage](oracle/i18n/servlet/localesource/HttpAcceptLanguage.md) extends [LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) implements Serializable

  - ### Class [oracle.i18n.servlet.localesource.LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream s)
                             throws IOException,
                                    ClassNotFoundException

        Reads the serialized form to construct this object
        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O exception occurs

        [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true) - if no corresponding class is found for the serialized form.

      - #### writeObject

            private void writeObject(ObjectOutputStream s)
                              throws IOException

        Writes this object into the serialized form
        Serial Data:
        Cache-able, Read-only, validated flags, followed by the parameter values in the order of Parameter.toArray.

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true) - if I/O exception occurs

    - ### Serialized Fields

      - #### m_isCached

            boolean m_isCached

      - #### m_isReadOnly

            boolean m_isReadOnly

      - #### m_isValidated

            boolean m_isValidated

  - ### Class [oracle.i18n.servlet.localesource.LocaleSource.Alignment](oracle/i18n/servlet/localesource/LocaleSource.Alignment.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### m_name

            String m_name

  - ### Class [oracle.i18n.servlet.localesource.LocaleSource.WritingDirection](oracle/i18n/servlet/localesource/LocaleSource.WritingDirection.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### m_name

            String m_name

  - ### Class oracle.i18n.servlet.localesource.Standalone extends [LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) implements Serializable

  - ### Class [oracle.i18n.servlet.localesource.UserInput](oracle/i18n/servlet/localesource/UserInput.md) extends [LocaleSource](oracle/i18n/servlet/localesource/LocaleSource.md) implements Serializable

- ## Package oracle.i18n.text

  - ### Class oracle.i18n.text.OraBoot extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### languageIdMap

            HashMap languageIdMap

      - #### territoryIdMap

            HashMap territoryIdMap

      - #### linguisticIdMap

            HashMap linguisticIdMap

      - #### charSetIdMap

            HashMap charSetIdMap

      - #### tableIdMap

            HashMap tableIdMap

      - #### idtoLanguageMap

            HashMap idtoLanguageMap

      - #### idtoTerritoryMap

            HashMap idtoTerritoryMap

      - #### idtoCharSetMap

            HashMap idtoCharSetMap

      - #### idtoLinguisticMap

            HashMap idtoLinguisticMap

      - #### idtoTableMap

            HashMap idtoTableMap

      - #### oraShortToOraLangMap

            HashMap oraShortToOraLangMap

      - #### oraLangToOraShortMap

            Map oraLangToOraShortMap

      - #### idtoCharSetMaxLen

            Map idtoCharSetMaxLen

      - #### langToTerrMap

            Map langToTerrMap

      - #### langToLingMap

            Map langToLingMap

      - #### langToCharSetsUnix

            Map langToCharSetsUnix

      - #### langToCharSetsWin

            Map langToCharSetsWin

      - #### lstCharSetIsAscii

            List lstCharSetIsAscii

      - #### lstCharSetIsEbcdic

            List lstCharSetIsEbcdic

      - #### lstCharSetIsFixed

            List lstCharSetIsFixed

      - #### lstCharSetIsStorage

            List lstCharSetIsStorage

      - #### availableLang

            String[] availableLang

      - #### availableTerr

            String[] availableTerr

      - #### availableCharSet

            String[] availableCharSet

      - #### availableLing

            String[] availableLing

  - ### Class [oracle.i18n.text.OraDateFormat](oracle/i18n/text/OraDateFormat.md) extends [Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### calendar

            Calendar calendar

        The calendar that this `OraDateFormat` object uses to calculate the date/time field values. Subclasses should initialize the `calendar` object accordingly based on the locale associated with this `OraDateFormat` object.

  - ### Class [oracle.i18n.text.OraDateFormatSymbols](oracle/i18n/text/OraDateFormatSymbols.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### amPmStrings

            String[] amPmStrings

      - #### decimalSeparator

            char decimalSeparator

      - #### eras

            String[] eras

      - #### groupingSeparator

            char groupingSeparator

      - #### months

            String[] months

      - #### shortMonths

            String[] shortMonths

      - #### weekdays

            String[] weekdays

      - #### shortWeekdays

            String[] shortWeekdays

      - #### capMonth

            boolean capMonth

      - #### capShortMonth

            boolean capShortMonth

      - #### capDay

            boolean capDay

      - #### capShortDay

            boolean capShortDay

      - #### upperEra

            boolean upperEra

      - #### upperAmPm

            boolean upperAmPm

      - #### monthLength

            int monthLength

      - #### shortMonthLength

            int shortMonthLength

      - #### weekdayLength

            int weekdayLength

      - #### shortWeekdayLength

            int shortWeekdayLength

      - #### amPmLength

            int amPmLength

      - #### eraLength

            int eraLength

  - ### Class [oracle.i18n.text.OraDecimalFormat](oracle/i18n/text/OraDecimalFormat.md) extends [OraNumberFormat](oracle/i18n/text/OraNumberFormat.md) implements Serializable

    - ### Serialized Fields

      - #### useDefaultPattern

            boolean useDefaultPattern

      - #### oraDecPatPos

            oracle.i18n.text.OraDecimalFormatPattern oraDecPatPos

      - #### oraDecPatNeg

            oracle.i18n.text.OraDecimalFormatPattern oraDecPatNeg

      - #### ora_lang

            String ora_lang

      - #### ora_terr

            String ora_terr

      - #### symbols

            OraDecimalFormatSymbols symbols

      - #### decimalSeparatorShown

            boolean decimalSeparatorShown

  - ### Class [oracle.i18n.text.OraDecimalFormatSymbols](oracle/i18n/text/OraDecimalFormatSymbols.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### currencySymbol

            String currencySymbol

      - #### decimalSeparator

            char decimalSeparator

      - #### groupingSeparator

            char groupingSeparator

      - #### internationalCurrencySymbol

            String internationalCurrencySymbol

      - #### infinity

            char infinity

      - #### NaN

            char NaN

  - ### Class oracle.i18n.text.OraDefaultDecimalFormatPattern extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### pattern

            String pattern

      - #### internalFormat

            int internalFormat

      - #### numberFractionDigits

            int numberFractionDigits

      - #### keepLeadingZero

            boolean keepLeadingZero

      - #### keepTrailingZero

            boolean keepTrailingZero

      - #### groupingSizes

            String groupingSizes

  - ### Class oracle.i18n.text.OraLanguage extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### VERSION

            String VERSION

      - #### INFO

            String INFO

      - #### Name

            String Name

      - #### Id

            String Id

      - #### DefaultTerritoryId

            String DefaultTerritoryId

      - #### DefaultCharSetId

            String DefaultCharSetId

      - #### DefaultLinguisticId

            String DefaultLinguisticId

      - #### NumberSpellingId

            String NumberSpellingId

      - #### CapitalizeMonthInitialChar

            String CapitalizeMonthInitialChar

      - #### CapitalizeDayInitialChar

            String CapitalizeDayInitialChar

      - #### WritingDirection

            String WritingDirection

      - #### ISOAbbreviation

            String ISOAbbreviation

      - #### SundayAbbreviation

            String SundayAbbreviation

      - #### MondayAbbreviation

            String MondayAbbreviation

      - #### TuesdayAbbreviation

            String TuesdayAbbreviation

      - #### WednesdayAbbreviation

            String WednesdayAbbreviation

      - #### ThursdayAbbreviation

            String ThursdayAbbreviation

      - #### FridayAbbreviation

            String FridayAbbreviation

      - #### SaturdayAbbreviation

            String SaturdayAbbreviation

      - #### SundayFullname

            String SundayFullname

      - #### MondayFullname

            String MondayFullname

      - #### TuesdayFullname

            String TuesdayFullname

      - #### WednesdayFullname

            String WednesdayFullname

      - #### ThursdayFullname

            String ThursdayFullname

      - #### FridayFullname

            String FridayFullname

      - #### SaturdayFullname

            String SaturdayFullname

      - #### Month01Abbreviation

            String Month01Abbreviation

      - #### Month02Abbreviation

            String Month02Abbreviation

      - #### Month03Abbreviation

            String Month03Abbreviation

      - #### Month04Abbreviation

            String Month04Abbreviation

      - #### Month05Abbreviation

            String Month05Abbreviation

      - #### Month06Abbreviation

            String Month06Abbreviation

      - #### Month07Abbreviation

            String Month07Abbreviation

      - #### Month08Abbreviation

            String Month08Abbreviation

      - #### Month09Abbreviation

            String Month09Abbreviation

      - #### Month10Abbreviation

            String Month10Abbreviation

      - #### Month11Abbreviation

            String Month11Abbreviation

      - #### Month12Abbreviation

            String Month12Abbreviation

      - #### Month01Fullname

            String Month01Fullname

      - #### Month02Fullname

            String Month02Fullname

      - #### Month03Fullname

            String Month03Fullname

      - #### Month04Fullname

            String Month04Fullname

      - #### Month05Fullname

            String Month05Fullname

      - #### Month06Fullname

            String Month06Fullname

      - #### Month07Fullname

            String Month07Fullname

      - #### Month08Fullname

            String Month08Fullname

      - #### Month09Fullname

            String Month09Fullname

      - #### Month10Fullname

            String Month10Fullname

      - #### Month11Fullname

            String Month11Fullname

      - #### Month12Fullname

            String Month12Fullname

      - #### AffirmativeResponse

            String AffirmativeResponse

      - #### NegativeResponse

            String NegativeResponse

      - #### AMString

            String AMString

      - #### PMString

            String PMString

      - #### ADString

            String ADString

      - #### BCString

            String BCString

      - #### NonInitialChar

            String NonInitialChar

      - #### NonFinalChar

            String NonFinalChar

      - #### DanglingChar

            String DanglingChar

      - #### CommonTerritories

            String[] CommonTerritories

      - #### CommonCharsets

            String[] CommonCharsets

      - #### CommonCharsetsWin

            String[] CommonCharsetsWin

      - #### CommonLinguisticSorts

            String[] CommonLinguisticSorts

  - ### Class oracle.i18n.text.OraLinguistic extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### VERSION

            String VERSION

        Version of the NLT file

      - #### SORTNAME

            String SORTNAME

        SORTNAME of this NLT file

      - #### SORTID

            int SORTID

        SORTID of this NLT file

      - #### BASESORTNAME

            String BASESORTNAME

        BASESORTNAME of this NLT file

      - #### BASESORTID

            int BASESORTID

        BASESORTID of this NLT file

      - #### Canonical_equivalence

            boolean Canonical_equivalence

        Flag to indicate if this sort rule supports canonical equivalence

      - #### Reverse_secondary

            boolean Reverse_secondary

        Flag to indicate if this sort rule supports secondary reverse

      - #### Swap_with_next

            boolean Swap_with_next

        Flag to indicate if this sort rule supports swapping with next

      - #### Hangul_jamo_composition

            boolean Hangul_jamo_composition

        Flag to indicate if this sort rule supports Hangul Jamo composition

      - #### collationLevel1

            int[] collationLevel1

        main collation table first level

      - #### collationLevel2

            int[] collationLevel2

        main collation table second level

      - #### contractCollKey

            int[] contractCollKey

        contracting table, collation key array

      - #### contractNumOfFE

            byte[] contractNumOfFE

        contracting table, number of following entries array

      - #### contractConChar

            char[][] contractConChar

        contracting table, contracting characters array

      - #### expandExpCharKey

            int[][] expandExpCharKey

        expanding table

      - #### contextPrevCpt

            int[] contextPrevCpt

        context sensitive table, previous codepoints array

      - #### contextCollKey

            int[] contextCollKey

        context sensitive table, collation key array

      - #### contextSenChar

            char[] contextSenChar

        context sensitive table, character array

      - #### contextNumOfFE

            char[] contextNumOfFE

        context sensitive table, number of following entries array

      - #### surrogateTable

            int[][] surrogateTable

        16 surrogate table

      - #### baseLetterTable

            oracle.i18n.util.builder.UnicodeMapChar baseLetterTable

        For monolingual -- base letter table

      - #### monolingual

            boolean monolingual

        Flag to indicate if this is monolingual rule

      - #### LatinOneTable

            int[][] LatinOneTable

        Latin One Table

  - ### Class oracle.i18n.text.OraMapTable extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### VERSION

            String VERSION

      - #### Name

            String Name

      - #### Id

            String Id

      - #### mapTable

            HashMap mapTable

      - #### attrTable

            Map attrTable

  - ### Class [oracle.i18n.text.OraNumberFormat](oracle/i18n/text/OraNumberFormat.md) extends [Format](http://docs.oracle.com/javase/8/docs/api/java/text/Format.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### SQLImplicit

            boolean SQLImplicit

      - #### groupingUsed

            boolean groupingUsed

      - #### parseIntegerOnly

            boolean parseIntegerOnly

      - #### maximumIntegerDigits

            int maximumIntegerDigits

      - #### minimumIntegerDigits

            int minimumIntegerDigits

      - #### maximumFractionDigits

            int maximumFractionDigits

      - #### minimumFractionDigits

            int minimumFractionDigits

  - ### Class [oracle.i18n.text.OraSimpleDateFormat](oracle/i18n/text/OraSimpleDateFormat.md) extends [OraDateFormat](oracle/i18n/text/OraDateFormat.md) implements Serializable

    - ### Serialized Fields

      - #### locale

            Locale locale

      - #### oraDatePat

            oracle.i18n.text.OraDateFormatPattern oraDatePat

      - #### symbols

            OraDateFormatSymbols symbols

  - ### Class oracle.i18n.text.OraTerritory extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### VERSION

            String VERSION

      - #### INFO

            String INFO

      - #### Name

            String Name

      - #### Id

            String Id

      - #### StartDayOfTheWeek

            String StartDayOfTheWeek

      - #### NegativeSignLocation

            String NegativeSignLocation

      - #### ISOWeekFlag

            String ISOWeekFlag

      - #### MetricMeasurementFlag

            String MetricMeasurementFlag

      - #### RoundingIndicator

            String RoundingIndicator

      - #### MinAccountingUnit

            String MinAccountingUnit

      - #### InternationalMonetaryFraction

            String InternationalMonetaryFraction

      - #### MonetaryFraction

            String MonetaryFraction

      - #### DebitSignFlag

            String DebitSignFlag

      - #### CreditSignFlag

            String CreditSignFlag

      - #### CurrencyDebitCreditFlag

            String CurrencyDebitCreditFlag

      - #### ISOAbbreviation

            String ISOAbbreviation

      - #### DecimalCharacter

            String DecimalCharacter

      - #### GroupSeparator

            String GroupSeparator

      - #### NumberDigitsForNumberGrouping

            String NumberDigitsForNumberGrouping

      - #### InternationalCurrencySymbol

            String InternationalCurrencySymbol

      - #### LocalCurrencySymbol

            String LocalCurrencySymbol

      - #### DecimalMonetaryChar

            String DecimalMonetaryChar

      - #### MonetaryGroupSeparator

            String MonetaryGroupSeparator

      - #### NumberDigitsForMonetaryGrouping

            String NumberDigitsForMonetaryGrouping

      - #### ListSeparator

            String ListSeparator

      - #### DebitSymbol

            String DebitSymbol

      - #### CreditSymbol

            String CreditSymbol

      - #### InternationalCurrencySeparator

            String InternationalCurrencySeparator

      - #### DateTimeFormatString

            String DateTimeFormatString

      - #### DateFormatString

            String DateFormatString

      - #### TimeFormatString

            String TimeFormatString

      - #### OracleDateFormatString

            String OracleDateFormatString

      - #### OracleTimeFormatString

            String OracleTimeFormatString

      - #### UnionCurrencySymbol

            String UnionCurrencySymbol

      - #### NLSTimeFormatString

            String NLSTimeFormatString

      - #### NLSTimestampFormatString

            String NLSTimestampFormatString

      - #### NLSTimeAndTimezoneFormatString

            String NLSTimeAndTimezoneFormatString

      - #### NLSTimestampAndTimezoneFormatString

            String NLSTimestampAndTimezoneFormatString

      - #### NLSTimeShortFormat

            String NLSTimeShortFormat

      - #### NLSDateShortFormat

            String NLSDateShortFormat

      - #### NLSDateLongFormat

            String NLSDateLongFormat

      - #### NLSNumberFormatPositive

            oracle.i18n.text.OraDefaultDecimalFormatPattern NLSNumberFormatPositive

      - #### NLSNumberFormatNegative

            oracle.i18n.text.OraDefaultDecimalFormatPattern NLSNumberFormatNegative

      - #### NLSCurrencyFormatPositive

            oracle.i18n.text.OraDefaultDecimalFormatPattern NLSCurrencyFormatPositive

      - #### NLSCurrencyFormatNegative

            oracle.i18n.text.OraDefaultDecimalFormatPattern NLSCurrencyFormatNegative

      - #### CommonLanguages

            String[] CommonLanguages

      - #### CommonTimeZones

            String[] CommonTimeZones

  - ### Class [oracle.i18n.text.OraUnicodeProperty](oracle/i18n/text/OraUnicodeProperty.md) extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### charConvCache

            HashMap charConvCache

  - ### Class oracle.i18n.text.SortedCommonLocales extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ### Serialized Fields

      - #### locArray

            Locale[] locArray

  - ### Class oracle.i18n.text.SortedLanguages extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ### Serialized Fields

      - #### langArray

            String[] langArray

  - ### Class oracle.i18n.text.SortedTerritories extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://docs.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws:
        [`IOException`](http://docs.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ### Serialized Fields

      - #### terrArray

            String[] terrArray

- ## Package oracle.i18n.util

  - ### Class oracle.i18n.util.HashTree extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### valueTable

            HashMap valueTable

      - #### sortedVector

            Vector sortedVector

      - #### htable

            HashMap[] htable

      - #### valueFreePtr

            int valueFreePtr

      - #### levelPtr

            int[] levelPtr

      - #### levelFreePtr

            int[] levelFreePtr

      - #### level

            char[][] level

      - #### levelChecker

            char[][] levelChecker

      - #### value

            char[][] value

  - ### Class oracle.i18n.util.UnicodeCatTable extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### unicodeData

            Hashtable unicodeData

      - #### sortedVector

            Vector sortedVector

      - #### htable1

            Hashtable htable1

      - #### htable2

            Hashtable htable2

      - #### htable3

            Hashtable htable3

      - #### level2

            int[] level2

      - #### level3

            int[] level3

      - #### level4

            int[] level4

      - #### level1

            int[] level1

      - #### level2Indexer

            int[][] level2Indexer

      - #### level3Indexer

            int[][] level3Indexer

      - #### level4Indexer

            int[][] level4Indexer

      - #### level2IndexerPt

            int level2IndexerPt

      - #### level3IndexerPt

            int level3IndexerPt

      - #### level4IndexerPt

            int level4IndexerPt

  - ### Class oracle.i18n.util.UnicodeDecompTree extends [Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ### Serialized Fields

      - #### decompIndex

            oracle.i18n.util.UnicodeCatTable decompIndex

      - #### decompLeaf

            int[] decompLeaf

      - #### excluDecompPT

            int excluDecompPT

      - #### compatDecompPT

            int compatDecompPT

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
