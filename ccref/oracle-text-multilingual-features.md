## D  Oracle Text Multilingual Features

This Appendix describes the multilingual features of Oracle Text. The following topics are discussed:

- Introduction

- Indexing

- Querying

- Supplied Stop Lists

- Knowledge Base

- Multilingual Features Matrix

### D.1 Introduction

This appendix summarizes the main multilingual features for Oracle Text.

For a complete list of Oracle Globalization Support languages and character set support, refer to the [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md).

**Note:**

Oracle Text does not support the `NLS_COMP` and `NLS_SORT` parameters. Search results generated from Oracle Text are independent from values of those parameters.

In Oracle Database 12c Release 2 (12.2), an Oracle Text index cannot be created on a column with a declared collation other than `BINARY`, `USING_NLS_COMP`, `USING_NLS_SORT` or `USING_NLS_SORT_CS`. For all the supported collations, the Oracle Text behavior is the same.

### D.2 Indexing

The following sections describe the multilingual indexing features:

- Multilingual Features for Text Index Types

- Lexer Types

- Basic Lexer Features

- Multi Lexer Features

- World Lexer Features

#### D.2.1 Multilingual Features for Text Index Types

The following sections describes the supported multilingual features for the Oracle Text index types.

- CONTEXT Index Type

- CTXCAT Index Type

- CTXRULE Index Type

**See Also:**

"Lexer Types" for a description of available lexers

##### D.2.1.1 CONTEXT Index Type

The `CONTEXT` index type fully supports multilingual features, including use of the language and character set columns.

The following lexers are supported:

- `AUTO_LEXER`

- `BASIC_LEXER`

- `MULTI_LEXER`

- `USER_LEXER`

- `WORLD_LEXER`

- `CHINESE_LEXER`

- `CHINESE_VGRAM_LEXER`

- `JAPANESE_LEXER`

- `JAPANESE_VGRAM_LEXER`

- `KOREAN_MORPH_LEXER`

##### D.2.1.2 CTXCAT Index Type

`CTXCAT` supports the multilingual features of the `BASIC_LEXER` with the exception of indexing themes, and supports the following additional lexers:

- `USER_LEXER`

- `WORLD_LEXER`

`CTXCAT` also supports the following lexers:

- `CHINESE_LEXER`

- `CHINESE_VGRAM_LEXER`

- `JAPANESE_LEXER`

- `JAPANESE_VGRAM_LEXER`

- `KOREAN_MORPH_LEXER`

##### D.2.1.3 CTXRULE Index Type

The `CTXRULE` index type supports the multilingual features of the `BASIC_LEXER` including `ABOUT` and `STEM` operators. It also supports Japanese, Chinese, and Korean (when used with the `SVM_CLASSIFIER`).

#### D.2.2 Lexer Types

Oracle Text supports the indexing of different languages by enabling you to choose a lexer in the indexing process. The specified lexer determines the languages you can index.

Table D-1 Oracle Text Lexer Types

| Lexer                | Supported Languages                                                                                                                                                                                                                                                                  |
|:---------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUTO_LEXER`         | Automatically identifies the language being indexed by examining the content, and applies suitable options (including stemming) for that language. Works best where each document contains a single-language, and has at least a couple of paragraphs of text to aid identification. |
| `BASIC_LEXER`        | Extracts tokens from text in languages, such as English and most of the western European languages that use space-delimited words.                                                                                                                                                   |
| `MULTI_LEXER`        | Indexes tables containing documents of different languages such as English, German, and Japanese.                                                                                                                                                                                    |
| `CHINESE_VGRAM`      | Extracts tokens from Chinese text.                                                                                                                                                                                                                                                   |
| `CHINESE_LEXER`      | Extracts tokens from Chinese text. This lexer offers the following benefits over the `CHINESE_VGRAM` lexer:<br>• Generates a smaller index<br>• Better query response time<br>• Generates real world tokens resulting in better query precision<br>• Supports stop words             |
| `JAPANESE_VGRAM`     | Extracts tokens from Japanese text.                                                                                                                                                                                                                                                  |
| `JAPANESE_LEXER`     | Extracts tokens from Japanese text. This lexer offers the following advantages over the `JAPANESE_VGRAM` lexer:<br>• Generates smaller index<br>• Better query response time<br>• Generates real world tokens resulting in better precision                                          |
| `KOREAN_MORPH_LEXER` | Extracts tokens from Korean text.                                                                                                                                                                                                                                                    |
| `USER_LEXER`         | Indexes a particular language.                                                                                                                                                                                                                                                       |
| `WORLD_LEXER`        | Indexes tables containing documents of different languages; autodetects languages in a document                                                                                                                                                                                      |

#### D.2.3 Basic Lexer Features

The following features are supported with the `BASIC_LEXER` preference. Enable these features with attributes of the `BASIC_LEXER`. Features such as alternate spelling, composite, and base letter can be enabled together for better search results.

- Theme Indexing

- Alternate Spelling

- Base Letter Conversion

- Composite

- Index stems

##### D.2.3.1 Theme Indexing

Enables the indexing and subsequent querying of document concepts with the `ABOUT` operator with `CONTEXT` index types. These concepts are derived from the Oracle Text knowledge base. This feature is supported for English and French.

This feature is not supported with `CTXCAT` index types.

##### D.2.3.2 Alternate Spelling

This feature enables you to search on alternate spellings of words. For example, with alternate spelling enabled in German, a query on gross returns documents that contain groß and gross.

This feature is supported in German, Danish, and Swedish.

Additionally, German can be indexed according to both traditional and reformed spelling conventions.

**See Also:**

"[Alternate Spelling](oracle-text-alternative-spelling.md)" and "[New German Spelling](oracle-text-alternative-spelling.md)".

##### D.2.3.3 Base Letter Conversion

This feature enables you to query words with or without diacritical marks such as tildes, accents, and umlauts. For example, with a Spanish base-letter index, a query of energia matches documents containing both energía and energia.

This feature is supported for English and all other supported whitespace delimited languages. In English and French, you can use the basic lexer to enable theme indexing.

**See Also:**

"[Base-Letter Conversion](oracle-text-alternative-spelling.md)"

##### D.2.3.4 Composite

This feature enables you to search on words that contain the specified term as a sub-composite. You must use the stem (\$) operator. This feature is supported for German and Dutch.

For example, in German, a query of \$register finds documents that contain Bruttoregistertonne and Registertonne.

##### D.2.3.5 Index stems

This feature enables you to specify a stemmer for stem indexing. Tokens are stemmed to a single base form at index time in addition to the normal forms. Specifying index stems enables better query performance for stem queries, for example \$computed.

This feature is supported for English, Dutch, French, German, Italian, and Spanish.

#### D.2.4 Multi Lexer Features

The `MULTI_LEXER` lexer enables you to index a column that contains documents of different languages. During indexing Oracle Text examines the language column and switches in the language-specific lexer to process the document. Define the lexer preferences for each language before indexing.

The multi lexer enables you to set different preferences for languages. For example, you can have `composite` set to `TRUE` for German documents and `composite` set to `FALSE` for Dutch documents.

#### D.2.5 World Lexer Features

Like `MULTI_LEXER`, the `WORLD_LEXER` lexer enables you to index documents that contain different languages. It automatically detects the languages of a document and, therefore, does not require you to create a language column in the base table.

`WORLD_LEXER` processes all database character sets and supports the Unicode 5.0 standard. For `WORLD_LEXER` to be effective with documents that use multiple languages, AL32UTF-8 or UTF8 Oracle character set encoding must be specified. This includes supplementary, or "surrogate-pair," characters.

Table D-2 and Table D-3 show the languages supported by `WORLD_LEXER`. This list may change as the Unicode standard changes, and in any case should not be considered exhaustive. (Languages are grouped by Unicode writing system, not by natural language groupings.)

Table D-2 Languages Supported by the World Lexer (Space-separated)

| Language Group     | Languages Include                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Arabic             | Arabic, Farsi, Kurdish, Pashto, Sindhi, Urdu                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Armenian           | Armenian                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Bengali            | Assamese, Bengali                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Bopomofo           | Hakka Chinese, Minnan Chinese                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Cyrillic           | Over 50 languages, including Belorussian, Bulgarian, Macedonian, Moldavian, Russian, Serbian, Serbo-Croatian, Ukrainian                                                                                                                                                                                                                                                                                                                                                                                              |
| Devenagari         | Bhojpuri, Bihari, Hindi, Kashmiri, Marathi, Nepali, Pali, Sanskrit                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Ethiopic           | Amharic, Ge'ez, Tigrinya, Tigre                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Georgian           | Georgian                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Greek              | Greek                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Gujarati           | Gujarati, Kacchi                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Gurmukhi           | Punjabi                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Hebrew             | Hebrew, Ladino, Yiddish                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Kaganga            | Redjang                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Kannada            | Kanarese, Kannada                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Korean             | Korean, Hanja Hangul                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Latin              | Afrikaans, Albanian, Basque, Breton, Catalan, Croatian, Czech, Danish, Dutch, English, Esperanto, Estonian, Faeroese, Fijian, Finnish, Flemish, French, Frisian, German, Hawaiian, Hungarian, Icelandic, Indonesian, Irish, Italian, Lappish, Classic Latin, Latvian, Lithuanian, Malay, Maltese, Pinyin Mandarin, Maori, Norwegian, Polish, Portuguese, Provencal, Romanian, Rumanian, Samoan, Scottish Gaelic, Slovak, Slovene, Slovenian, Sorbian, Spanish, Swahili, Swedish, Tagalog, Turkish, Vietnamese, Welsh |
| Malayalam          | Malayalam                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Mongolian          | Mongolian                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Oriya              | Oriya                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Sinhalese, Sinhala | Pali, Sinhalese                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Syriac             | Aramaic, Syriac                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Tamil              | Tamil                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Telugu             | Telugu                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Thaana             | Dhiveli, Divehi, Maldivian                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

Table D-3 Languages Supported by the World Lexer (Non-space-separated)

| Language Group | Languages Include                      |
|:---------------|:---------------------------------------|
| Chinese        | Cantonese, Mandarin, Pinyin phonograms |
| Japanese       | Japanese (Hiragana, Kanji, Katakana)   |
| Khmer          | Cambodian, Khmer                       |
| Lao            | Lao                                    |
| Myanmar        | Burmese                                |
| Thai           | Thai                                   |
| Tibetan        | Dzongkha, Tibetan                      |

Table D-4 shows languages not supported by the World Lexer.

Table D-4 Languages Not Supported by the World Lexer

| Language Group               | Languages Include                                                                                      |
|:-----------------------------|:-------------------------------------------------------------------------------------------------------|
| Buhid                        | Buhid                                                                                                  |
| Canadian Syllabics           | Blackfoot, Carrier, Cree, Dakhelh, Inuit, Inuktitut, Naskapi, Nunavik, Nunavut, Ojibwe, Sayisi, Slavey |
| Cherokee                     | Cherokee                                                                                               |
| Cypriot                      | Cypriot                                                                                                |
| Limbu                        | Limbu                                                                                                  |
| Ogham                        | Ogham                                                                                                  |
| Runic                        | Runic                                                                                                  |
| Tai Le (Tai Lu, Lue, Dai Le) | Tai Le                                                                                                 |
| Ugaritic                     | Ugaritic                                                                                               |
| Yi                           | Yi                                                                                                     |
| Yi Jang Hexagram             | Yi Jang                                                                                                |

### D.3 Querying

Oracle Text supports the use of different query operators. Some operators can be set to behave in accordance with your language. This section summarizes the multilingual query features for these operators.

- Use the `ABOUT` operator to query on concepts. The system looks up concept information in the theme component of the index. This feature is supported for English and French with `CONTEXT` indexes only.

- The fuzzy operator enables you to search for words that have similar spelling to specified word. Oracle Text supports `fuzzy` for English, French, German, Italian, Dutch, Spanish, Portuguese, Japanese, Optical Character recognition (OCR), and automatic language detection.

- The stem operator enables you to search for words that have the same root as the specified term. For example, a stem of \$sing expands into a query on the words sang, sung, sing. The Oracle Text stemmer supports the following languages: English, French, Spanish, Italian, German, Japanese and Dutch.

### D.4 Supplied Stoplists

By default, the system indexes text using the system-supplied stoplist that corresponds to your database language.

A stoplist is a list of words that do not get indexed. These are usually common words in a language such as this, that, and can in English.

Oracle Text provides a default stoplist for English, Chinese (traditional and simplified), Danish, Dutch, Finnish, French, German, Italian, Portuguese, Spanish, and Swedish.

**Related Topics**

- [Oracle Text Supplied Stoplists](oracle-text-supplied-stoplists.md)

### D.5 Knowledge Base

An Oracle Text knowledge base is a hierarchical tree of concepts used for theme indexing, `ABOUT` queries, and deriving themes for document services.

Oracle Text supplies knowledge bases in English and French only. These knowledge bases are installed by default.

You can extend theme functionality to languages other than English or French by loading your own knowledge base for any single byte white space delimited language, including Spanish.

### D.6 Multilingual Features Matrix

The following table summarizes the multilingual features for the supported languages.

Table D-5 Multilingual Features for Supported Languages

| LANGUAGE            | ALTERNATE SPELLING | FUZZY MATCHING | LANGUAGE SPECIFIC LEXER | DEFAULT STOP LIST | STEMMING |
|:--------------------|:-------------------|:---------------|:------------------------|:------------------|:---------|
| ENGLISH             | N/A                | Yes            | Yes                     | Yes               | Yes      |
| GERMAN              | Yes                | Yes            | Yes                     | Yes               | Yes      |
| JAPANESE            | N/A                | Yes            | Yes                     | No                | Yes      |
| FRENCH              | N/A                | Yes            | Yes                     | Yes               | Yes      |
| SPANISH             | N/A                | Yes            | Yes                     | Yes               | Yes      |
| ITALIAN             | N/A                | Yes            | Yes                     | Yes               | Yes      |
| DUTCH               | N/A                | Yes            | Yes                     | Yes               | Yes      |
| PORTUGUESE          | N/A                | Yes            | Yes                     | Yes               | Yes      |
| KOREAN              | N/A                | No             | Yes                     | No                | Yes      |
| SIMPLIFIED CHINESE  | N/A                | No             | Yes                     | Yes               | Yes      |
| TRADITIONAL CHINESE | N/A                | No             | Yes                     | Yes               | Yes      |
| DANISH              | Yes                | No             | Yes                     | No                | Yes      |
| SWEDISH             | Yes                | No             | Yes                     | Yes               | Yes      |
| FINNISH             | N/A                | No             | Yes                     | No                | Yes      |
| ARABIC              | N/A                | No             | Yes                     | No                | Yes      |
| GREEK               | N/A                | No             | Yes                     | No                | Yes      |
| BOKMAL              | N/A                | No             | Yes                     | No                | Yes      |
| POLISH              | N/A                | No             | Yes                     | No                | Yes      |
| RUSSIAN             | N/A                | No             | Yes                     | No                | Yes      |
| SLOVENIAN           | N/A                | No             | Yes                     | No                | Yes      |
| THAI                | N/A                | No             | Yes                     | No                | Yes      |
| CATALAN             | N/A                | No             | Yes                     | No                | Yes      |
| CROATIAN            | N/A                | No             | Yes                     | No                | Yes      |
| HEBREW              | N/A                | No             | Yes                     | No                | Yes      |
| NYNORSK             | N/A                | No             | Yes                     | No                | Yes      |
| SERBIAN             | N/A                | No             | Yes                     | No                | Yes      |
| TURKISH             | N/A                | No             | Yes                     | No                | Yes      |
| CZECH               | N/A                | No             | Yes                     | No                | Yes      |
| HUNGARIAN           | N/A                | No             | Yes                     | No                | Yes      |
| PERSIAN             | N/A                | No             | Yes                     | No                | Yes      |
| SLOVAK              | N/A                | No             | Yes                     | No                | Yes      |
