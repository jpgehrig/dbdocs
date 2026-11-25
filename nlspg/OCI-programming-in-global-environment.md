## 10  OCI Programming in a Global Environment

This chapter contains information about OCI programming in a globalized environment. This chapter includes the following topics:

- Using the OCI NLS Functions

- Specifying Character Sets in OCI

- Getting Locale Information in OCI

- Mapping Locale Information Between Oracle and Other Standards

- Manipulating Strings in OCI

- Classifying Characters in OCI

- Converting Character Sets in OCI

- OCI Messaging Functions

- lmsgen Utility

### 10.1 Using the OCI NLS Functions

Many OCI NLS functions accept one of the following handles:

- The environment handle

- The user session handle

The OCI environment handle is associated with the client NLS environment and initialized with the client NLS environment variables. This environment does not change when `ALTER` `SESSION` statements are issued to the server. The character set associated with the environment handle is the client character set.

The OCI session handle is associated with the server session environment. Its NLS settings change when the session environment is modified with an `ALTER` `SESSION `statement. The character set associated with the session handle is the database character set.

Note that the OCI session handle does not have any NLS settings associated with it until the first transaction begins in the session. `SELECT` statements do not begin a transaction.

**See Also:**

[Oracle Call Interface Programmer's Guide ](../lnoci/oci-globalization-support-functions.md)for detailed information about the OCI NLS functions

### 10.2 Specifying Character Sets in OCI

Use the `OCIEnvNlsCreate` function to specify client-side database and national character sets when the OCI environment is created. This function enables users to set character set information dynamically in applications, independent of the `NLS_LANG` and `NLS_NCHAR` initialization parameter settings. In addition, one application can initialize several environment handles for different client environments in the same server environment.

Any Oracle character set ID except AL16UTF16 can be specified through the `OCIEnvNlsCreate` function to specify the encoding of metadata, SQL `CHAR` data, and SQL `NCHAR` data. Use `OCI_UTF16ID` in the `OCIEnvNlsCreate` function to specify UTF-16 data.

**See Also:**

[Oracle Call Interface Programmer's Guide ](../lnoci/oci-globalization-support-functions.md)for more information about the `OCIEnvNlsCreate` function

### 10.3 Getting Locale Information in OCI

An Oracle locale consists of language, territory, and character set definitions. The locale determines conventions such as day and month names, as well as date, time, number, and currency formats. A globalized application complies with a user's locale setting and cultural conventions. For example, when the locale is set to German, users expect to see day and month names in German.

You can use the `OCINlsGetInfo()` function to retrieve the following locale information:

-  Days of the week (translated)
-  Abbreviated days of the week (translated)
-  Month names (translated)
-  Abbreviated month names (translated)
-  Yes/no (translated)
-  AM/PM (translated)
-  AD/BC (translated)
-  Numeric format
-  Debit/credit
-  Date format
-  Currency formats
-  Default language
-  Default territory
-  Default character set
-  Default linguistic sort
-  Default calendar

Table 10-1 summarizes OCI functions that return locale information.

Table 10-1 OCI Functions That Return Locale Information

| Function                         | Description                                                                                    |
|:---------------------------------|:-----------------------------------------------------------------------------------------------|
| `OCINlsGetInfo()`                | Returns locale information. See preceding text.                                                |
| `OCINlsCharSetNameTold()`        | Returns the Oracle character set ID for the specified Oracle character set name                |
| `OCINlsCharSetIdToName()`        | Returns the Oracle character set name from the specified character set ID                      |
| `OCINlsNumericInfoGet()`         | Returns specified numeric information such as maximum character size                           |
| `OCINlsEnvironmentVariableGet()` | Returns the character set ID from `NLS_LANG` or the national character set ID from `NLS_NCHAR` |

**See Also:**

[Oracle Call Interface Programmer's Guide ](../lnoci/oci-globalization-support-functions.md)

### 10.4 Mapping Locale Information Between Oracle and Other Standards

The `OCINlsNameMap` function maps Oracle character set names, language names, and territory names to and from Internet Assigned Numbers Authority (IANA) and International Organization for Standardization (ISO) names.

### 10.5 Manipulating Strings in OCI

Two types of data structures are supported for string manipulation:

- Native character strings

- Wide character strings

Native character strings are encoded in native Oracle character sets. Functions that operate on native character strings take the string as a whole unit with the length of the string calculated in bytes. Wide character (`wchar`) string functions provide more flexibility in string manipulation. They support character-based and string-based operations with the length of the string calculated in characters.

The wide character data type is Oracle-specific and should not be confused with the `wchar_t` data type defined by the ANSI/ISO C standard. The Oracle wide character data type is always 4 bytes in all platforms, while the size of `wchar_t` depends on the implementation and the platform. The Oracle wide character data type normalizes native characters so that they have a fixed width for easy processing. This guarantees no data loss for round-trip conversion between the Oracle wide character format and the native character format.

String manipulation includes the:

- Conversion of strings between native character format and wide character format

- Character classifications

- Case conversion

- Calculations of display length

- General string manipulation, such as comparison, concatenation, and searching

Table 10-2 summarizes the OCI string manipulation functions.

**Note:**

The functions and descriptions in Table 10-2 that refer to multibyte strings apply to native character strings.

Table 10-2 OCI String Manipulation Functions

| Function                          | Description                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCIMultiByteToWideChar()`        | Converts an entire null-terminated string into the `wchar` format.                                                                                                                                                                                                                                                                                                                                     |
| `OCIMultiByteInSizeToWideChar()`  | Converts part of a string into the `wchar` format.                                                                                                                                                                                                                                                                                                                                                     |
| `OCIWideCharToMultiByte()`        | Converts an entire null-terminated wide character string into a multibyte string.                                                                                                                                                                                                                                                                                                                      |
| `OCIWideCharInSizeToMultiByte()`  | Converts part of a wide character string into the multibyte format.                                                                                                                                                                                                                                                                                                                                    |
| `OCIWideCharToLower()`            | Converts the `wchar` character specified by `wc` into the corresponding lowercase character if it exists in the specified locale. If no corresponding lowercase character exists, then it returns `wc` itself.                                                                                                                                                                                         |
| `OCIWideCharToUpper()`            | Converts the `wchar` character specified by `wc` into the corresponding uppercase character if it exists in the specified locale. If no corresponding uppercase character exists, then it returns `wc` itself.                                                                                                                                                                                         |
| `OCIWideCharStrcmp()`             | Compares two wide character strings by binary, linguistic, or case-insensitive comparison method.<br>Note: The `UNICODE_BINARY` sort method cannot be used with `OCIWideCharStrcmp()` to perform a linguistic comparison of the supplied wide character arguments.                                                                                                                                     |
| `OCIWideCharStrncmp()`            | Similar to `OCIWideCharStrcmp()`. Compares two wide character strings by binary, linguistic, or case-insensitive comparison methods. At most `len1` bytes form `str1`, and `len2` bytes form `str2`.<br>Note: As with `OCIWideCharStrcmp()`, the `UNICODE_BINARY` sort method cannot be used with `OOCIWideCharStrncmp()` to perform a linguistic comparison of the supplied wide character arguments. |
| `OCIWideCharStrcat()`             | Appends a copy of the string pointed to by `wsrcstr`. Then it returns the number of characters in the resulting string.                                                                                                                                                                                                                                                                                |
| `OCIWideCharStrncat()`            | Appends a copy of the string pointed to by `wsrcstr`. Then it returns the number of characters in the resulting string. At most `n` characters are appended.                                                                                                                                                                                                                                           |
| `OCIWideCharStrchr()`             | Searches for the first occurrence of `wc` in the string pointed to by `wstr`. Then it returns a pointer to the `wchar` if the search is successful.                                                                                                                                                                                                                                                    |
| `OCIWideCharStrrchr()`            | Searches for the last occurrence of `wc` in the string pointed to by `wstr`.                                                                                                                                                                                                                                                                                                                           |
| `OCIWideCharStrcpy()`             | Copies the `wchar` string pointed to by `wsrcstr` into the array pointed to by `wdststr`. Then it returns the number of characters copied.                                                                                                                                                                                                                                                             |
| `OCIWideCharStrncpy()`            | Copies the `wchar` string pointed to by `wsrcstr` into the array pointed to by `wdststr`. Then it returns the number of characters copied. At most `n` characters are copied from the array.                                                                                                                                                                                                           |
| `OCIWideCharStrlen()`             | Computes the number of characters in the `wchar` string pointed to by `wstr` and returns this number.                                                                                                                                                                                                                                                                                                  |
| `OCIWideCharStrCaseConversion()`  | Converts the wide character string pointed to by `wsrcstr` into the case specified by a flag and copies the result into the array pointed to by `wdststr`.                                                                                                                                                                                                                                             |
| `OCIWideCharDisplayLength()`      | Determines the number of column positions required for `wc` in display.                                                                                                                                                                                                                                                                                                                                |
| `OCIWideCharMultibyteLength()`    | Determines the number of bytes required for `wc` in multibyte encoding.                                                                                                                                                                                                                                                                                                                                |
| `OCIMultiByteStrcmp()`            | Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods.                                                                                                                                                                                                                                                                                                          |
| `OCIMultiByteStrncmp()`           | Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods. At most `len1` bytes form `str1` and `len2` bytes form `str2.`.                                                                                                                                                                                                                                          |
| `OCIMultiByteStrcat()`            | Appends a copy of the multibyte string pointed to by `srcstr`.                                                                                                                                                                                                                                                                                                                                         |
| `OCIMultiByteStrncat()`           | Appends a copy of the multibyte string pointed to by `srcstr`. At most `n` bytes from `srcstr` are appended to `dststr`.                                                                                                                                                                                                                                                                               |
| `OCIMultiByteStrcpy()`            | Copies the multibyte string pointed to by `srcstr` into an array pointed to by `dststr`. It returns the number of bytes copied.                                                                                                                                                                                                                                                                        |
| `OCIMultiByteStrncpy()`           | Copies the multibyte string pointed to by `srcstr` into an array pointed to by `dststr`. It returns the number of bytes copied. At most `n` bytes are copied from the array pointed to by `srcstr` to the array pointed to by `dststr`.                                                                                                                                                                |
| `OCIMultiByteStrlen()`            | Returns the number of bytes in the multibyte string pointed to by `str`.                                                                                                                                                                                                                                                                                                                               |
| `OCIMultiByteStrnDisplayLength()` | Returns the number of display positions occupied by the complete characters within the range of `n` bytes.                                                                                                                                                                                                                                                                                             |
| `OCIMultiByteStrCaseConversion()` | Converts part of a string from one character set to another.                                                                                                                                                                                                                                                                                                                                           |

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-globalization-support-functions.md)

### 10.6 Classifying Characters in OCI

Table 10-3 shows the OCI character classification functions.

Table 10-3 OCI Character Classification Functions

| Function                    | Description                                                                 |
|:----------------------------|:----------------------------------------------------------------------------|
| `OCIWideCharIsAlnum()`      | Tests whether the wide character is an alphabetic letter or decimal digit   |
| `OCIWideCharIsAlpha()`      | Tests whether the wide character is an alphabetic letter                    |
| `OCIWideCharIsCntrl()`      | Tests whether the wide character is a control character                     |
| `OCIWideCharIsDigit()`      | Tests whether the wide character is a decimal digit                         |
| `OCIWideCharIsGraph()`      | Tests whether the wide character is a graph character                       |
| `OCIWideCharIsLower()`      | Tests whether the wide character is a lowercase letter                      |
| `OCIWideCharIsPrint()`      | Tests whether the wide character is a printable character                   |
| `OCIWideCharIsPunct()`      | Tests whether the wide character is a punctuation character                 |
| `OCIWideCharIsSpace()`      | Tests whether the wide character is a space character                       |
| `OCIWideCharIsUpper()`      | Tests whether the wide character is an uppercase character                  |
| `OCIWideCharIsXdigit()`     | Tests whether the wide character is a hexadecimal digit                     |
| `OCIWideCharIsSingleByte()` | Tests whether `wc` is a single-byte character when converted into multibyte |

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-globalization-support-functions.md)

### 10.7 Converting Character Sets in OCI

Conversion between Oracle character sets and Unicode (16-bit, fixed-width Unicode encoding) is supported. Replacement characters are used if a character has no mapping from Unicode to the Oracle character set. Therefore, conversion back to the original character set is not always possible without data loss.

Table 10-4 summarizes the OCI character set conversion functions.

Table 10-4 OCI Character Set Conversion Functions

| Function                                  | Description                                                                                                                                                                 |
|:------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCICharSetToUnicode()`                   | Converts a multibyte string pointed to by `src` to Unicode into the array pointed to by `dst`                                                                               |
| `OCIUnicodeToCharSet()`                   | Converts a Unicode string pointed to by `src` to multibyte into the array pointed to by `dst`                                                                               |
| `OCINlsCharSetConvert()`                  | Converts a string from one character set to another                                                                                                                         |
| `OCICharSetConversionIsReplacementUsed()` | Indicates whether replacement characters were used for characters that could not be converted in the last invocation of `OCINlsCharSetConvert()` or `OCIUnicodeToCharSet()` |

**See Also:**

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-globalization-support-functions.md)

- "[OCI Programming with Unicode](programming-with-unicode.md)"

### 10.8 OCI Messaging Functions

The user message API provides a simple interface for cartridge developers to retrieve their own messages as well as Oracle messages.

Table 10-5 summarizes the OCI messaging functions.

Table 10-5 OCI Messaging Functions

| Function            | Description                                                                                                                                                           |
|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCIMessageOpen()`  | Opens a message handle in a language pointed to by `hndl`                                                                                                             |
| `OCIMessageGet()`   | Retrieves a message with message number identified by `msgno`. If the buffer is not zero, then the function copies the message into the buffer specified by `msgbuf`. |
| `OCIMessageClose()` | Closes a message handle pointed to by `msgh` and frees any memory associated with this handle                                                                         |

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-programming-basics.md)

### 10.9 lmsgen Utility

#### Purpose

The `lmsgen` utility converts text-based message files (`.msg`) into binary format (`.msb`) so that Oracle messages and OCI messages provided by the user can be returned to OCI functions in the desired language.

Messages used by the server are stored in binary-format files that are placed in the `$ORACLE_HOME/product_name/mesg` directory, or the equivalent for your operating system. Multiple versions of these files can exist, one for each supported language, using the following file name convention:

    <product_id><language_abbrev>.msb

For example, the file containing the server messages in French is called `oraf.msb`, because `ORA` is the product ID (\<`product_id`\>) and `F` is the language abbreviation (\<`language_abbrev`\>) for French. The value for `product_name` is rdbms, so it is in the `$ORACLE_HOME/rdbms/mesg` directory.

#### Syntax

    LMSGEN text_file product facility [language] [-i indir] [-o outdir]

- `text_file` is a message text file.
- `product` is the name of the product.
- `facility` is the name of the facility.
- `language` is the optional message language corresponding to the language specified in the `NLS_LANG` parameter. The language parameter is required if the message file is not tagged properly with language.
- `indir` is the optional directory to specify the text file location.
- `outdir` is the optional directory to specify the output file location.

The output (`.msb`) file will be generated under the `$ORACLE_HOME/product/mesg/` directory.

#### Text Message Files

Text message files must follow these guidelines:

- Lines that start with `/` and `//` are treated as internal comments and are ignored.

- To tag the message file with a specific language, include a line similar to the following:

<!-- -->

        #   CHARACTER_SET_NAME= Japanese_Japan.JA16EUC

- Each message contains three fields:

<!-- -->

         message_number, warning_level, message_text

- The message number must be unique within a message file.
- The warning level is not currently used. Use `0`.
- The message text cannot be longer than 511 bytes.

The following example shows an Oracle message text file:

    / Copyright (c) 2006 by Oracle.  All rights reserved.
    / This is a test us7ascii message file
    # CHARACTER_SET_NAME= american_america.us7ascii
    /
    00000, 00000, "Export terminated unsuccessfully\n"
    00003, 00000, "no storage definition found for segment(%lu, %lu)"

#### Example: Creating a Binary Message File from a Text Message File

The following table contains sample values for the `lmsgen` parameters:

| Parameter   | Value       |
|:------------|:------------|
| `product`   | `myapp`     |
| `facility`  | `imp`       |
| `language`  | `AMERICAN`  |
| `text_file` | `impus.msg` |

One of the lines in the text message file is the following:

    00128,2, "Duplicate entry %s found in %s"

The `lmsgen` utility converts the text message file (`impus.msg`) into binary format, resulting in a file called `impus.msb`. The directory `$ORACLE_HOME/myapp/mesg` must already exist.

    % lmsgen impus.msg myapp imp AMERICAN

The following output results:

    Generating message file impus.msg -->
    $ORACLE_HOME/myapp/mesg/impus.msb
