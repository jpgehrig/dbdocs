## Glossary

### accent

A mark that changes the sound of a character. Because the common meaning of the word accent is associated with the stress or prominence of the character's sound, the preferred word in Oracle Database Globalization Support Guide is diacritic.

See also diacritic.

### accent-insensitive linguistic sort

A linguistic sort that uses information only about base letters, not diacritics or case.

See also linguistic collation, base letter, diacritic, case.

### AL16UTF16

The default Oracle Database character set for the SQL `NCHAR` data type, which is used for the national character set. It encodes Unicode data in the UTF-16BE (big endian) encoding scheme.

See also national character set, UTF-16.

### AL32UTF8

An Oracle Database character set for the SQL `CHAR` data type, which is used for the database character set. It encodes Unicode data in the UTF-8 encoding scheme.

Starting from Oracle Database 12c Release 2, if you use Oracle Universal Installer (OUI) or Oracle Database Configuration Assistant (DBCA) to create a database, then the default database character set used is AL32UTF8.

See also database character set.

### ASCII

American Standard Code for Information Interchange. A common encoded 7-bit character set for English. ASCII includes the letters A-Z and a-z, as well as digits, punctuation symbols, and control characters. The Oracle Database character set name is US7ASCII.

### base letter

A character stripped of its diacritics and case. For example, the base letter for `a`, `A`, `ä`, and `Ä` is `a`.

See also diacritic.

### binary collation

A type of collation that orders strings based on their binary representation (character encoding), treating each string as a simple sequences of bytes.

See also collation, linguistic collation, monolingual linguistic collation, multilingual linguistic collation, accent-insensitive linguistic sort, case-insensitive linguistic collation.

### binary sorting

Ordering character strings using the binary collation.

### byte semantics

Treatment of strings as a sequence of bytes. Offsets into strings and string lengths are expressed in bytes.

See also character semantics and length semantics.

### canonical equivalence

A Unicode Standard term for describing that two characters or sequences of characters are to be semantically considered as the same character. Canonically equivalent characters cannot be distinguished when they are correctly rendered. For example, the precomposed character ñ (U+00F1 Latin Small Letter N With Tilde) is canonically equivalent to the sequence n (U+006E Latin Small Letter N) followed by ˜ (U+0303 Combining Tilde).

### case

Refers to the condition of being uppercase or lowercase. For example, in a Latin alphabet, `A` is the uppercase form for `a`, which is the lowercase form.

### case conversion

Changing a character from uppercase to lowercase or vice versa.

### case-insensitive linguistic collation

A linguistic collation that uses information about base letters and diacritics but not case but not when determining the ordering of strings.

See also base letter, case, diacritic, linguistic collation.

### character

A character is an abstract element of text. A character is different from a glyph, which is a specific representation of a character. For example, the first character of the English upper-case alphabet can be displayed as monospaced A, proportional italic AA, cursive (longhand) A, and so on. These forms are different glyphs that represent the same character. A character, a character code, and a glyph are related as follows:

character --(encoding)--\> character code --(font)--\> glyph

For example, the first character of the English uppercase alphabet is represented in computer memory as a number. The number is called the encoding or the character code. The character code for the first character of the English uppercase alphabet is 0x41 in the ASCII encoding scheme. The character code is 0xc1 in the EBCDIC encoding scheme.

You must choose a font to display or print the character. The available fonts depend on which encoding scheme is being used. Each font will usually use a different shape, that is, a different glyph to represent the same character.

See also character code and glyph.

### character classification

Information that provides details about the type of character associated with each character code. For example, a character can be uppercase, lowercase, punctuation, or control character.

### character code

A character code is a sequence of bytes that represents a specific character. The sequence depends on the character encoding scheme. For example, the character code of the first character of the English uppercase alphabet is 0x41 in the ASCII encoding scheme, but it is 0xc1 in the EBCDIC encoding scheme.

See also character.

### character encoding form

A rule that assigns numbers to all characters in a character set.

### character encoding scheme

A rule that maps numbers assigned by the character encoding form to particular sequences of bytes (character codes). For example, the UTF-16 encoding form has the big-endian encoding scheme (UTF-16BE) and the little-endian encoding scheme (UTF-16LE).

Most encoding forms have only one encoding scheme. Therefore, encoding form, encoding scheme, and encoding are often used interchangeably.

Oracle character sets correspond to character encoding schemes. For example, AL16UTF16 is the Oracle name for the UTF-16BE encoding scheme.

### character repertoire

The characters that are available to be used, or encoded, in a specific character set.

### character semantics

Treatment of strings as a sequence of characters. Offsets into strings and string lengths are expressed in characters (character codes).

See also byte semantics and length semantics.

### character set

A collection of elements that represent textual information for a specific language or group of languages. One language can be represented by more than one character set.

A character set does not always imply a specific character encoding scheme. A character encoding scheme is the assignment of a character code to each character in a character set.

In this manual, a character set usually does imply a specific character encoding scheme. Therefore, a character set is the same as an encoded character set in this manual.

### character set migration

Changing the character set of an existing database.

### character string

A sequence of characters.

A character string can also contain no characters. In this case, the character string is called a null string. The number of characters in a null string is 0 (zero).

### client character set

The encoded character set used by the database client. A client character set can differ from the database character set. The database character set is sometimes called the server character set. If the client character set is different from the database character set, then character set conversion must occur.

See also database character set.

### code point

The numeric representation of a character in a character set. For example, the code point of `A` in the ASCII character set is 0x41. The code point of a character is also called the encoded value of a character.

See also Unicode code point.

### code unit

The unit of encoded text for processing and interchange. The size of the code unit varies depending on the character encoding scheme. In most character encodings, a code unit is 1 byte. Important exceptions are UTF-16 and UCS-2, which use 2-byte code units, and wide character, which uses 4 bytes.

See also character encoding form.

### collation

Ordering of character strings according to rules about sorting characters that are associated with a language in a specific locale. Also called linguistic sort.

See also linguistic collation, monolingual linguistic collation, multilingual linguistic collation, accent-insensitive linguistic sort, case-insensitive linguistic collation.

### data scanning

The process of identifying potential problems with character set conversion and truncation of data before migrating the database character set.

### database character set

The encoded character set that is used to store text in the database. This includes `CHAR`, `VARCHAR2`, `LONG`, and fixed-width `CLOB` column values and all SQL and PL/SQL text.

### Database Migration Assistant for Unicode (DMU)

An intuitive and user-friendly GUI tool to migrate your character set. It helps you streamline the migration process through an interface that minimizes the workload and ensures that all migration issues are addressed.

### diacritic

A mark near or through a character or combination of characters that indicates a different sound than the sound of the character without the diacritical mark. For example, the cedilla in `façade` is a diacritic. It changes the sound of `c`.

### EBCDIC

Extended Binary Coded Decimal Interchange Code. EBCDIC is a family of encoded character sets used mostly on IBM mainframe systems.

### encoded character set

A character set with an associated character encoding scheme. An encoded character set specifies the byte sequence (character code) that is assigned to each character.

See also character encoding form.

### encoded value

The numeric representation of a character in a character set. For example, the code point of `A` in the ASCII character set is 0x41. The encoded value of a character is also called the code point of a character.

### font

An ordered collection of character glyphs that provides a graphical representation of characters in a character set.

### globalization

The process of making software suitable for different linguistic and cultural environments. Globalization should not be confused with localization, which is the process of preparing software for use in one specific locale (for example, translating error messages or user interface text from one language to another).

### glyph

A glyph (font glyph) is a specific representation (shape) of a character. A character can have many different glyphs.

See also character.

### ideograph

A symbol that represents an idea. Some writing systems use ideographs to represent words through their meaning instead of using letters to represent words through their sound. Chinese is an example of an ideographic writing system.

### ISO

International Organization for Standardization. A worldwide federation of national standards bodies from 130 countries. The mission of ISO is to develop and promote standards in the world to facilitate the international exchange of goods and services.

### ISO 8859

A family of 8-bit encoded character sets. The most common one is ISO 8859-1 (also known as ISO Latin1), and is used for Western European languages.

### ISO 14651

A multilingual linguistic collation standard that is designed for almost all languages of the world.

See also multilingual linguistic collation.

### ISO/IEC 10646

A universal character set standard that defines the characters of most major scripts used in the modern world. ISO/IEC 10646 is kept synchronized with the Unicode Standard as far as character repertoire is concerned but it defines fewer properties and fewer text processing algorithms than the Unicode Standard.

### ISO currency

The 3-letter abbreviation used to denote a local currency, based on the ISO 4217 standard. For example, `USD` represents the United States dollar.

### ISO Latin1

The ISO 8859-1 character set standard. It is an 8-bit extension to ASCII that adds 128 characters that include the most common Latin characters used in Western Europe. The Oracle Database character set name is WE8ISO8859P1.

See also ISO 8859.

### length semantics

Length semantics determines how you treat the length of a character string. The length can be expressed as a number of characters (character codes) or as a number of bytes in the string.

See also character semantics and byte semantics.

### linguistic collation

A type of collation that takes into consideration the standards and customs of spoken languages.

See also collation, linguistic sorting, monolingual linguistic collation, multilingual linguistic collation, accent-insensitive linguistic sort, case-insensitive linguistic collation.

### linguistic index

An index built on a linguistic sort order.

### linguistic sorting

Ordering character strings using a linguistic binary collation.

See also multilingual linguistic collation and monolingual linguistic collation.

### locale

A collection of information about the linguistic and cultural preferences from a particular region. Typically, a locale consists of language, territory, character set, linguistic, and calendar information defined in NLS data files.

### localization

The process of providing language-specific or culture-specific information for software systems. Translation of an application's user interface is an example of localization. Localization should not be confused with globalization, which is the making software suitable for different linguistic and cultural environments.

### monolingual linguistic collation

An Oracle Database collation that has two levels of comparison for strings. String are first ordered based on major values for their characters and if they are found equal in this comparison, they are further ordered based on minor values of their characters. Major values correspond roughly to base letters while minor values correspond to diacritics and case. Most European languages can be sorted with a monolingual collation, but monolingual collations are inadequate for Asian languages and for multilingual text.

See also multilingual linguistic collation.

### monolingual support

Support for only one language.

### multibyte

Two or more bytes.

When character codes are assigned to all characters in a specific language or a group of languages, one byte (8 bits) can represent 256 different characters. Two bytes (16 bits) can represent up to 65,536 different characters. Two bytes are not enough to represent all the characters for many languages. Some characters require 3 or 4 bytes.

One example is the UTF-8 Unicode encoding form. In UTF-8, there are many 2-byte and 3-byte characters.

Another example is Traditional Chinese, used in Taiwan. It has more than 80,000 characters. Some character encoding schemes that are used in Taiwan use 4 bytes to encode characters.

See also single byte.

### multibyte character

A character whose character code consists of two or more bytes under a certain character encoding scheme.

Note that the same character may have different character codes under different encoding schemes. Oracle Database cannot tell whether a character is a multibyte character without knowing which character encoding scheme is being used. For example, Japanese Hankaku-Katakana (half-width Katakana) characters are one byte in the JA16SJIS encoded character set, two bytes in JA16EUC, and three bytes in AL32UTF8.

See also single-byte character.

### multibyte character string

A character string encoded in a multibyte character encoding scheme.

### multibyte character encoding scheme

A character encoding scheme in which character codes may have more than one byte.

See also multibyte fixed-width character encoding scheme, multibyte varying-width character encoding scheme.

### multibyte fixed-width character encoding scheme

A character encoding scheme in which each character code has the same fixed number of bytes, greater than one. AL16UTF16 is a multibyte fixed-width character set.

### multibyte varying-width character encoding scheme

A character encoding scheme in which each character code has a number of bytes from a given range. The range is one to the maximum character width of the character set. Depending on the encoding scheme, the maximum character width of the character set may be 2, 3, or 4 bytes. For example, ZHT16BIG5 has character codes with one or two bytes. UTF8 has character codes with one, two, or three bytes. AL32UTF8 has character codes with one, two, three, or four bytes. Oracle does not support encoding schemes with more than 4 bytes per character code.

### multilingual linguistic collation

An Oracle Database collation that evaluates strings on three levels. Asian languages require a multilingual linguistic collation even if data exists in only one language. Multilingual linguistic collations are also used when data exists in several languages.

In multilingual collations, strings are first ordered based on primary weights, then, if necessary, secondary weights, then tertiary weights. For letters, primary weights correspond to base letters, secondary weights to diacritics, and tertiary weights to case and specific decoration, such as circle around the character. For ideographic scripts weights may represent other character variations.

### national character set

An alternate character set from the database character set that can be specified for `NCHAR`, `NVARCHAR2`, and `NCLOB` columns. National character sets are AL16UTF16 and UTF8 only.

### NLB files

Binary files used by the Locale Builder to define locale-specific data. They define all of the locale definitions that are shipped with a specific release of Oracle Database. You can create user-defined NLB files with Oracle Locale Builder.

See also Oracle Locale Builder and NLT files.

### NLS

National Language Support. NLS enables users to interact with the database in their native languages. It also enables applications to run in different linguistic and cultural environments. The term has been replaced by the terms globalization and localization.

### NLSRTL

National Language Support Runtime Library. This library is responsible for providing locale-independent algorithms for internationalization. The locale-specific information (that is, NLSDATA) is read by the NLSRTL library during run-time.

### NLT files

Text files used by the Locale Builder to define locale-specific data. Because they are in text, you can view the contents.

### null string

A character string that contains no characters.

### Oracle Locale Builder

A GUI utility that offers a way to view, modify, or define locale-specific data.

### replacement character

A character used during character conversion when the source character is not available in the target character set. For example, `?` (question mark) is often used as the default replacement character in Oracle character sets.

### restricted multilingual support

Multilingual support that is restricted to a group of related languages.Western European languages can be represented with ISO 8859-1, for example, but the use of ISO 8859-1 restricts the multilingual support. Thai or Chinese could not be added to the group.

### SQL CHAR data types

Includes `CHAR`, `VARCHAR`, `VARCHAR2`, `CLOB`, and `LONG` data types.

### SQL NCHAR data types

Includes `NCHAR`, `NVARCHAR2`, and `NCLOB` data types.

### script

A particular system of writing. A collection of related graphic symbols that are used in a writing system. Some scripts can represent multiple languages, and some languages use multiple scripts. Examples of scripts include Latin, Arabic, and Han.

### single byte

One byte. One byte usually consists of 8 bits. When character codes are assigned to all characters for a specific language, one byte (8 bits) can represent 256 different characters.

See also multibyte.

### single-byte character

A single-byte character is a character whose character code consists of one byte under a specific character encoding scheme. Note that the same character may have different character codes under different encoding schemes. Oracle Database cannot tell which character is a single-byte character without knowing which encoding scheme is being used. For example, the euro currency symbol is one byte in the WE8MSWIN1252 encoded character set, two bytes in AL16UTF16, and three bytes in UTF8.

See also multibyte character.

### single-byte character string

A single-byte character string is a string encoded in a single-byte character encoding scheme. The term may also be used to describe a multibyte varying-width character string that happens to consist only of single-byte character codes.See also multibyte varying-width character encoding scheme.

### sort

An ordering of strings. This can be based on requirements from a locale instead of the binary representation of the strings, which is called a linguistic sort, or based on binary coded values, which is called a binary sort.

See also multilingual linguistic collation and monolingual linguistic collation.

### supplementary characters

The first version of the Unicode Standard was a 16-bit, fixed-width encoding that used two bytes to encode each character. This enabled 65,536 characters to be represented. However, more characters need to be supported because of the large number of Asian ideograms.

Unicode Standard version 3.1 defined supplementary characters to meet this need by extending the numbering range for characters from 0000-FFFF hexadecimal to 0000-10FFFF hexadecimal. Unicode 3.1 began using two 16-bit code units (also known as surrogate pairs) to represent a single supplementary character in the UTF-16 form. This enabled an additional 1,048,576 characters to be defined. The Unicode 3.1 standard added the first group of 44,944 supplementary characters. More were added with subsequent versions of the Unicode Standard.

### surrogate pairs

See also supplementary characters.

### syllabary

Provide a mechanism for communicating phonetic information along with the ideographic characters used by languages such as Japanese.

### UCS-2

An obsolete form for an ISO/IEC 10646 standard character set encoding form. Currently used to mean the UTF-16 encoding form without support for surrogate pairs.

### UCS-4

An obsolete name for an ISO/IEC 10646 standard encoding form, synonymous with UTF-32.

### Unicode Standard

Unicode Standard is a universal encoded character set that enables information from any language to be stored by using a single character set. Unicode Standard provides a unique code value for every character, regardless of the platform, program, or language.

Unicode Standard also defines various text processing algorithms and related character properties to aid in complex script processing of scripts such as Arabic or Devanagari (Hindi).

### Unicode database

A database whose database character set is AL32UTF8 or UTF8.

### Unicode code point

A value in the Unicode codespace, which ranges from 0 to 0x10FFFF. Unicode assigns a unique code point to every character.

### Unicode data type

A SQL `NCHAR` data type (`NCHAR`, `NVARCHAR2`, and `NCLOB`). You can store Unicode characters in columns of these data types even if the database character set is not based on the Unicode Standard.

### unrestricted multilingual support

The ability to use as many languages as desired. A universal character set, such as Unicode Standard, helps to provide unrestricted multilingual support because it supports a very large character repertoire, encompassing most modern languages of the world.

### UTFE

An Oracle character set implementing a 4-byte subset of the Unicode UTF-EBCDIC encoding form, used only on EBCDIC platforms and deprecated.

### UTF8

The UTF8 Oracle character set encodes characters in one, two, or three bytes. The UTF8 character set supports Unicode 3.0 and implements the CESU-8 encoding scheme. Although specific supplementary characters were not assigned code points in Unicode until version 3.1, the code point range was allocated for supplementary characters in Unicode 3.0. Supplementary characters are treated as two separate, user-defined characters that occupy 6 bytes. UTF8 is deprecated.

### UTF-8

The 8-bit encoding form and scheme of the Unicode Standard. It is a multibyte varying-width encoding. One Unicode character can be 1 byte, 2 bytes, 3 bytes, or 4 bytes in the UTF-8 encoding. Characters from the European scripts are represented in either 1 or 2 bytes. Characters from most Asian scripts are represented in 3 bytes. Supplementary characters are represented in 4 bytes. The Oracle Database character set that implements UTF-8 is AL32UTF8.

### UTF-16

The 16-bit encoding form of Unicode. One Unicode character can be one or two 2-code units in the UTF-16 encoding. Characters (including ASCII characters) from European scripts and most Asian scripts are represented by one code unit (2 bytes). Supplementary characters are represented by two code units (4 bytes). The Oracle Database character sets that implement UTF-16 are AL16UTF16 and AL16UTF16LE. AL16UTF16 implements the big-endian encoding scheme of the UTF-16 encoding form (more significant byte of each code unit comes first in memory). AL16UTF16 is a valid national character set. AL16UTF16LE implements the little-endian UTF-16 encoding scheme. It is a conversion-only character set, valid only in character set conversion functions such as SQL `CONVERT` or PL/SQL `UTL_I18N.STRING_TO_RAW`.Note that most SQL string processing functionality treats each UTF-16 code unit in AL16UTF16 as a separate character. The functions `INSTR4`, `SUBSTR4`, and `LENGTH4` are an exception.

### wide character

A multibyte fixed-width character format that is useful for extensive text processing because it enables data to be processed in consistent, fixed-width chunks. Multibyte varying-width character values may be internally converted to the wide character format for faster processing.
