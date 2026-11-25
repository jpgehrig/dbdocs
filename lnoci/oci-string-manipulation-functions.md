Lists and describes OCI string manipulation functions.

Two types of data structures are supported for string manipulation:

- Multibyte strings

- Wide-character strings

Multibyte strings are encoded in native Oracle character sets. Functions that operate on multibyte strings take the string as a whole unit with the length of the string calculated in bytes. Wide-character (`wchar`) string functions provide more flexibility in string manipulation. They support character-based and string-based operations with the length of the string calculated in characters.

The wide-character data type is Oracle-specific and should not be confused with the `wchar_t` data type defined by the ANSI/ISO C standard. The Oracle wide-character data type is always 4 bytes in all operating systems, whereas the size of `wchar_t` depends on the implementation and the operating system. The Oracle wide-character data type normalizes multibyte characters so that they have a fixed width for easy processing. This guarantees no data loss for round-trip conversion between the Oracle wide-character set and the native character set.

String manipulation can be classified into the following categories:

- Conversion of strings between multibyte and wide character

- Character classifications

- Case conversion

- Calculations of display length

- General string manipulation, such as comparison, concatenation, and searching

Table 31-4 summarizes the OCI string manipulation functions, which are described in this section.

Table 31-4 OCI String Manipulation Functions

| Function                         | Purpose                                                                                                                             |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| OCIMultiByteInSizeToWideChar()   | Convert part of a multibyte string into the wide-character string                                                                   |
| OCIMultiByteStrCaseConversion()  | Convert a multibyte string into the specified case and copies the result into the destination array                                 |
| OCIMultiByteStrcat()             | Append a multibyte string to the destination string                                                                                 |
| OCIMultiByteStrcmp()             | Compare two multibyte strings by binary, linguistic, or case-insensitive comparison methods                                         |
| OCIMultiByteStrcpy()             | Copy a multibyte string into the destination array. It returns the number of bytes copied.                                          |
| OCIMultiByteStrlen()             | Return the number of bytes in a multibyte string                                                                                    |
| OCIMultiByteStrncat()            | Append, at most, n bytes from a multibyte string to the destination string                                                          |
| OCIMultiByteStrncmp()            | Compare two multibyte strings by binary, linguistic, or case-insensitive comparison methods. Each string is in the specified length |
| OCIMultiByteStrncpy()            | Copy a specified number of bytes of a multibyte string into the destination array                                                   |
| OCIMultiByteStrnDisplayLength()  | Return the number of display positions occupied by the multibyte string within the range of n bytes                                 |
| OCIMultiByteToWideChar()         | Convert a `NULL`-terminated multibyte string into wide-character format                                                             |
| "OCIWideCharInSizeToMultiByte()" | Convert part of a wide-character string to the multibyte string                                                                     |
| OCIWideCharMultiByteLength()     | Determine the number of bytes required for a wide character in multibyte encoding                                                   |
| OCIWideCharStrCaseConversion()   | Convert a wide-character string into the specified case and copies the result into the destination array                            |
| OCIWideCharStrcat()              | Append a wide-character string to the destination string                                                                            |
| OCIWideCharStrchr()              | Search for the first occurrence of a wide character in a string. Return a point to the wide character if the search is successful.  |
| OCIWideCharStrcmp()              | Compare two wide-character strings by binary, linguistic, or case-insensitive comparison methods                                    |
| OCIWideCharStrcpy()              | Copy a wide-character string into a destination array. Return the number of characters copied.                                      |
| OCIWideCharStrlen()              | Return the number of characters in a wide-character string                                                                          |
| OCIWideCharStrncat()             | Append, at most, n characters from a wide-character string to the destination string                                                |
| OCIWideCharStrncmp()             | Compare two wide-character strings by binary, linguistic, or case-insensitive methods. Each string is a specified length.           |
| OCIWideCharStrncpy()             | Copy, at most, n characters of a wide-character string into the destination array                                                   |
| OCIWideCharStrrchr()             | Search for the last occurrence of a character in a wide-character string                                                            |
| OCIWideCharToLower()             | Convert a specified wide character into the corresponding lowercase character                                                       |
| OCIWideCharToMultiByte()         | Convert a `NULL`-terminated wide-character string into a multibyte string                                                           |
| OCIWideCharToUpper()             | Convert a specified wide character into the corresponding uppercase character                                                       |

### 31.4.1 OCIMultiByteInSizeToWideChar()

Converts part of a multibyte string into the wide-character string.

#### Purpose

Converts part of a multibyte string into the wide-character string.

#### Syntax

    sword OCIMultiByteInSizeToWideChar ( void          *hndl,
                                         OCIWchar      *dst,
                                         size_t         dstsz,
                                         const OraText *src,
                                         size_t         srcsz,
                                         size_t        *rsize );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set of the string.

dst (OUT)
Pointer to a destination buffer for `wchar`. It can be a `NULL` pointer when `dstsz` is zero.

dstsz (IN)
Destination buffer size in number of characters. If it is zero, then this function returns the number of characters needed for the conversion.

src (IN)
Source string to be converted.

srcsz (IN)
Length of source string in bytes.

rsize (OUT)
Number of characters written into the destination buffer, or number of characters for the converted string if `dstsz` is zero. If it is a `NULL` pointer, then nothing is returned.

#### Comments

This routine converts part of a multibyte string into the wide-character string. It converts as many complete characters as it can until it reaches the output buffer size limit or input buffer size limit or it reaches a `NULL` terminator in a source string. The output buffer is `NULL`-terminated if space permits. If `dstsz` is zero, then this function returns only the number of characters not including the ending `NULL` terminator needed for a converted string. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIMultiByteToWideChar()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.2 OCIMultiByteStrCaseConversion()

Converts a multibyte string into the specified case and copies the result into the destination array.

#### Purpose

Converts the multibyte string pointed to by `srcstr` into uppercase or lowercase as specified by the flag and copies the result into the array pointed to by `dststr`.

#### Syntax

    size_t OCIMultiByteStrCaseConversion ( void           *hndl,
                                           OraText        *dststr,
                                           const OraText  *srcstr,
                                           ub4             flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle.

dststr (OUT)
Pointer to destination array. The result string is `NULL`-terminated.

srcstr (IN)
Pointer to source string.

flag (IN)
Specify the case to which to convert:

- `OCI_NLS_UPPERCASE`: Convert to uppercase.

- `OCI_NLS_LOWERCASE`: Convert to lowercase.

This flag can be used with `OCI_NLS_LINGUISTIC` to specify that the linguistic setting in the locale is used for case conversion.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes in the result string, not including the `NULL` terminator.

### 31.4.3 OCIMultiByteStrcat()

Appends a multibyte string to the destination string.

#### Purpose

Appends a copy of the multibyte string pointed to by `srcstr` to the end of the string pointed to by `dststr`.

#### Syntax

    size_t OCIMultiByteStrcat ( void            *hndl,
                                OraText         *dststr,
                                const OraText   *srcstr );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

dststr (IN/OUT)
Pointer to the destination multibyte string for appending. The output buffer is `NULL`-terminated.

srcstr (IN)
Pointer to the source string to append.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes in the result string, not including the `NULL` terminator.

**Related Topics**

- OCIMultiByteStrncat()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.4 OCIMultiByteStrcmp()

Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods.

#### Purpose

Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods.

#### Syntax

    int OCIMultiByteStrcmp ( void            *hndl,
                             const OraText   *str1,
                             const OraText   *str2,
                             int              flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle.

str1 (IN)
Pointer to a `NULL`-terminated string.

str2 (IN)
Pointer to a `NULL`-terminated string.

flag (IN)
It is used to decide the comparison method. It can take one of these values:

- `OCI_NLS_BINARY`: Binary comparison This is the default value.

- `OCI_NLS_LINGUISTIC`: Linguistic comparison specified in the locale.

This flag can be used with `OCI_NLS_CASE_INSENSITIVE` for case-insensitive comparison. For example, use `OCI_NLS_LINGUISTIC|OCI_NLS_CASE_INSENSITIVE` to compare strings linguistically without regard to case.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The return values for the function are:

- 0, if `str1 = str2`

- Positive, if `str1 > str2`

- Negative, if `str1 < str2`

**Related Topics**

- OCIMultiByteStrncmp()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.5 OCIMultiByteStrcpy()

Copies a multibyte string into the destination array. It returns the number of bytes copied.

#### Purpose

Copies the multibyte string pointed to by `srcstr` into the array pointed to by `dststr`.

#### Syntax

    size_t OCIMultiByteStrcpy ( void            *hndl,
                                OraText         *dststr,
                                const OraText   *srcstr );

#### Parameters

hndl (IN/OUT)
Pointer to the OCI environment or user session handle.

dststr (OUT)
Pointer to the destination buffer. The output buffer is `NULL`-terminated.

srcstr (IN)
Pointer to the source multibyte string.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes copied, not including the `NULL` terminator.

**Related Topics**

- OCIMultiByteStrncpy()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.6 OCIMultiByteStrlen()

Returns the number of bytes in a multibyte string.

#### Purpose

Returns the number of bytes in the multibyte string pointed to by `str`, not including the `NULL` terminator.

#### Syntax

    size_t OCIMultiByteStrlen ( void           *hndl,
                                const OraText  *str );

#### Parameters

hndl (IN/OUT)
Pointer to the OCI environment or user session handle.

str (IN)
Pointer to the source multibyte string.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes, not including the `NULL` terminator.

**Related Topics**

- OCIWideCharStrlen()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.7 OCIMultiByteStrncat()

Appends, at most, n bytes from a multibyte string to the destination string.

#### Purpose

Appends a specified number of bytes from a multibyte string to a destination string.

#### Syntax

    size_t OCIMultiByteStrncat ( void            *hndl,
                                 OraText         *dststr,
                                 const OraText   *srcstr,
                                 size_t           n );

#### Parameters

hndl (IN/OUT)
Pointer to OCI environment or user session handle.

dststr (IN/OUT)
Pointer to the destination multibyte string for appending.

srcstr (IN)
Pointer to the source multibyte string to append.

n (IN)
The number of bytes from `srcstr` to append.

#### Comments

This function is similar to `OCIMultiByteStrcat()`. At most, n bytes from `srcstr` are appended to `dststr`. Note that the `NULL` terminator in `srcstr` stops appending, and the function appends as many character as possible within `n` bytes. The `dststr` parameter is `NULL`-terminated. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes in the result string, not including the `NULL` terminator.

**Related Topics**

- OCIMultiByteStrcat()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.8 OCIMultiByteStrncmp()

Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods. Each string is in the specified length.

#### Purpose

Compares two multibyte strings by binary, linguistic, or case-insensitive comparison methods. A length is specified for each string.

#### Syntax

    int OCIMultiByteStrncmp ( void           *hndl,
                              const OraText  *str1,
                              size_t          len1,
                              OraText        *str2,
                              size_t          len2,
                              int             flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle.

str1 (IN)
Pointer to the first string.

len1 (IN)
The length of the first string to compare.

str2 (IN)
Pointer to the second string.

len2 (IN)
The length of the second string to compare.

flag (IN)
It is used to decide the comparison method. It can take one of these values:

- `OCI_NLS_BINARY`: Binary comparison. This is the default value.

- `OCI_NLS_LINGUISTIC`: Linguistic comparison specified in the locale.

This flag can be used with `OCI_NLS_CASE_INSENSITIVE` for case-insensitive comparison. For example, use `OCI_NLS_LINGUISTIC|OCI_NLS_CASE_INSENSITIVE` to compare strings linguistically without regard to case.

#### Comments

This function is similar to `OCIMultiByteStrcmp()`, except that, at most, `len1` bytes from `str1` and `len2` bytes from `str2` are compared. The `NULL` terminator is used in the comparison. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The return values for the function are:

- 0, if `str1` = `str2`

- Positive, if `str1` \> `str2`

- Negative, if `str1` \< `str2`

**Related Topics**

- OCIMultiByteStrcpy()
- OCIMultiByteStrncpy()
- OCIMultiByteStrcmp()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.9 OCIMultiByteStrncpy()

Copies a specified number of bytes of a multibyte string into the destination array.

#### Purpose

Copies a multibyte string into an array.

#### Syntax

    size_t OCIMultiByteStrncpy ( void            *hndl,
                                 OraText         *dststr,
                                 const OraText   *srcstr,
                                 size_t           n );

#### Parameters

hndl (IN/OUT)
Pointer to OCI environment or user session handle.

dststr (IN)
Pointer to the source multibyte string.

srcstr (OUT)
Pointer to the destination buffer.

n (IN)
The number of bytes from `srcstr` to copy.

#### Comments

This function is similar to `OCIMultiByteStrcpy()`. At most, n bytes are copied from the array pointed to by `srcstr` to the array pointed to by `dststr`. Note that the `NULL` terminator in `srcstr` stops copying, and the function copies as many characters as possible within `n` bytes. The result string is `NULL`-terminated. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes in the resulting string, not including the `NULL` terminator.

**Related Topics**

- OCIMultiByteStrcpy()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.10 OCIMultiByteStrnDisplayLength()

Returns the number of display positions occupied by the multibyte string within the range of n bytes.

#### Purpose

Returns the number of display positions occupied by the multibyte string within the range of `n` bytes.

#### Syntax

    size_t OCIMultiByteStrnDisplayLength ( void            *hndl,
                                           const OraText   *str1,
                                           size_t           n );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle.

str1 (IN)
Pointer to a multibyte string.

n (IN)
The number of bytes to examine.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of display positions.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.11 OCIMultiByteToWideChar()

Converts a `NULL`-terminated multibyte string into wide-character format.

#### Purpose

Converts an entire `NULL`-terminated string into the wide-character string.

#### Syntax

    sword OCIMultiByteToWideChar ( void            *hndl,
                                   OCIWchar        *dst,
                                   const OraText   *src,
                                   size_t          *rsize );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set of the string.

dst (OUT)
Destination buffer for `wchar`.

src (IN)
Source string to be converted.

rsize (OUT)
Number of characters converted, including `NULL` terminator. If it is a `NULL` pointer, then nothing is returned.

#### Comments

The `wchar` output buffer is `NULL`-terminated. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIWideCharToMultiByte()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.12 OCIWideCharInSizeToMultiByte()

Converts part of a wide-character string to the multibyte string.

#### Purpose

Converts part of a wide-character string to multibyte format.

#### Syntax

    sword OCIWideCharInSizeToMultiByte ( void             *hndl,
                                         OraText          *dst,
                                         size_t            dstsz,
                                         const OCIWchar   *src,
                                         size_t            srcsz,
                                         size_t           *rsize );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set of string.

dst (OUT)
Destination buffer for multibyte. It can be a `NULL` pointer if `dstsz` is zero.

dstsz (IN)
Destination buffer size in bytes. If it is zero, then the function returns the size in bytes need for converted string.

src (IN)
Source `wchar` string to be converted.

srcsz (IN)
Length of source string in characters.

rsize (OUT)
Number of bytes written into destination buffer, or number of bytes needed to store the converted string if `dstsz` is zero. If it is a `NULL` pointer, then nothing is returned.

#### Comments

Converts part of a wide-character string into the multibyte format. It converts as many complete characters as it can until it reaches the output buffer size or the input buffer size or until it reaches a `NULL` terminator in the source string. The output buffer is `NULL`-terminated if space permits. If `dstsz` is zero, then the function returns the size in bytes, not including the `NULL` terminator needed to store the converted string. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.13 OCIWideCharMultiByteLength()

Determines the number of bytes required for a wide character in multibyte encoding.

#### Purpose

Determines the number of bytes required for a wide character in multibyte encoding.

#### Syntax

    size_t OCIWideCharMultiByteLength ( void      *hndl,
                                        OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` character.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in function, then this function produces an error.

#### Returns

The number of bytes required for the wide character.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.14 OCIWideCharStrCaseConversion()

Converts a wide-character string into the specified case and copies the result into the destination array.

#### Purpose

Converts a wide-character string into a specified case and copies the result into the destination array.

#### Syntax

    size_t OCIWideCharStrCaseConversion ( void              *hndl,
                                          OraText           *dststr,
                                          const OraText     *srcstr,
                                          ub4                flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle.

dststr (OUT)
Pointer to destination array. The result string is `NULL`-terminated.

srcstr (IN)
Pointer to source string.

flag (IN)
Specify the case to which to convert:

- `OCI_NLS_UPPERCASE`: Convert to uppercase.

- `OCI_NLS_LOWERCASE`: Convert to lowercase.

This flag can be used with `OCI_NLS_LINGUISTIC` to specify that the linguistic setting in the locale is used for case conversion.

#### Comments

Converts the wide-character string pointed to by `srcstr` into uppercase or lowercase as specified by the flag and copies the result into the array pointed to by `dststr`. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of bytes in the result string, not including the `NULL` terminator.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.15 OCIWideCharStrcat()

Appends a wide-character string to the destination string.

#### Purpose

Appends the wide-character string pointed to by `wsrcstr` to the wide-character string pointed to by `wdststr`.

#### Syntax

    size_t OCIWideCharStrcat ( void             *hndl,
                               OCIWchar         *wdststr,
                               const OCIWchar   *wsrcstr );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wdststr (IN/OUT)
Pointer to the destination `wchar` string. The output buffer is `NULL`-terminated.

wsrcstr (IN)
Pointer to the source wide-character string to append.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of characters in the result string, not including the `NULL` terminator.

**Related Topics**

- OCIWideCharStrncat()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.16 OCIWideCharStrchr()

Searches for the first occurrence of a wide character in a string. Returns a point to the wide character if the search is successful.

#### Purpose

Searches for the first occurrence of a specified character in a wide-character string.

#### Syntax

    OCIWchar *OCIWideCharStrchr ( void             *hndl,
                                  const OCIWchar   *wstr,
                                  OCIWchar          wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wstr (IN)
Pointer to the `wchar` string to search.

wc (IN)
The `wchar` to search for.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

A `wchar` pointer if successful; otherwise, a `NULL` pointer.

**Related Topics**

- OCIWideCharStrrchr()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.17 OCIWideCharStrcmp()

Compares two wide-character strings by binary, linguistic, or case-insensitive comparison methods.

#### Purpose

Compares two wide-character strings by binary (based on `wchar` encoding value), linguistic, or case-insensitive comparison methods.

#### Syntax

    int OCIWideCharStrcmp ( void             *hndl,
                            const OCIWchar   *wstr1,
                            const OCIWchar   *wstr2,
                            int               flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wstr1 (IN)
Pointer to a `NULL`-terminated `wchar` string.

wstr2 (IN)
Pointer to a `NULL`-terminated `wchar` string.

flag (IN)
Used to decide the comparison method. It can take one of these values:

- `OCI_NLS_BINARY`: Binary comparison. This is the default value.

- `OCI_NLS_LINGUISTIC`: Linguistic comparison specified in the locale definition.

This flag can be used with `OCI_NLS_CASE_INSENSITIVE` for case-insensitive comparison. For example, use `OCI_NLS_LINGUISTIC|OCI_NLS_CASE_INSENSITIVE` to compare strings linguistically without regard to case.

The UNICODE_BINARY sort method cannot be used with `OCIWideCharStrcmp()` to perform a linguistic comparison of supplied wide-character arguments.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The return values for the function are:

- 0, if `wstr1 = wstr2`

- Positive, if `wstr1 > wstr2`

- Negative, if `wstr1 < wstr2`

**Related Topics**

- OCIWideCharStrncmp()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.18 OCIWideCharStrcpy()

Copies a wide-character string into a destination array. Returns the number of characters copied.

#### Purpose

Copies a wide-character string into an array.

#### Syntax

    size_t OCIWideCharStrcpy ( void             *hndl,
                               OCIWchar         *wdststr,
                               const OCIWchar   *wsrcstr );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wdststr (OUT)
Pointer to the destination `wchar` buffer. The result string is `NULL`-terminated.

wsrcstr (IN)
Pointer to the source `wchar` string.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of characters copied, not including the `NULL` terminator.

**Related Topics**

- OCIWideCharStrncpy()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.19 OCIWideCharStrlen()

Return the number of characters in a wide-character string.

#### Purpose

Returns the number of characters in a wide-character string.

#### Syntax

    size_t OCIWideCharStrlen ( void             *hndl,
                               const OCIWchar   *wstr );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wstr (IN)
Pointer to the source `wchar` string.

#### Comments

Returns the number of characters in the `wchar` string pointed to by `wstr`, not including the `NULL` terminator. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of characters, not including the `NULL` terminator.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.20 OCIWideCharStrncat()

Appends, at most, n characters from a wide-character string to the destination string.

#### Purpose

Appends, at most, n characters from a wide-character string to the destination.

#### Syntax

    size_t OCIWideCharStrncat ( void             *hndl,
                                OCIWchar         *wdststr,
                                const OCIWchar   *wsrcstr,
                                size_t            n );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wdststr (IN/OUT)
Pointer to the destination `wchar` string.

wsrcstr (IN)
Pointer to the source `wchar` string.

n (IN)
Number of characters from `wsrcstr` to append.

#### Comments

This function is similar to `OCIWideCharStrcat()`. At most, n characters from `wsrcstr` are appended to `wdststr`. Note that the `NULL` terminator in `wsrcstr` stops appending. The `wdststr` parameter is `NULL`-terminated. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of characters in the result string, not including the `NULL` terminator.

**Related Topics**

- OCIWideCharStrcat()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.21 OCIWideCharStrncmp()

Compares two wide-character strings by binary, linguistic, or case-insensitive methods. Each string is a specified length.

#### Purpose

Compares two wide-character strings by binary, linguistic, or case-sensitive methods. Each string has a specified length.

#### Syntax

    int OCIWideCharStrncmp ( void                *hndl,
                             const OCIWchar      *wstr1,
                             size_t               len1,
                             const OCIWchar      *wstr2,
                             size_t               len2,
                             int                  flag );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wstr1 (IN)
Pointer to the first `wchar` string.

len1 (IN)
The length from the first string for comparison.

wstr2 (IN)
Pointer to the second `wchar` string.

len2 (IN)
The length from the second string for comparison.

flag (IN)
It is used to decide the comparison method. It can take one of these values:

- `OCI_NLS_BINARY`: For the binary comparison, this is default value.

- `OCI_NLS_LINGUISTIC`: For the linguistic comparison specified in the locale.

This flag can be used with `OCI_NLS_CASE_INSENSITIVE` for case-insensitive comparison. For example, use `OCI_NLS_LINGUISTIC`\|`OCI_NLS_CASE_INSENSITIVE` to compare strings linguistically without regard to case.

#### Comments

This function is similar to `OCIWideCharStrcmp()`. It compares two wide-character strings by binary, linguistic, or case-insensitive comparison methods. At most, `len1` bytes from `wstr1` and `len2` bytes from `wstr2` are compared. The `NULL` terminator is used in the comparison. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

The UNICODE_BINARY sort method cannot be used with `OCIWideCharStrncmp()` to perform a linguistic comparison of supplied wide-character arguments.

#### Returns

The return values for the function are:

- 0, if `wstr1 = wstr2`

- Positive, if `wstr1 > wstr2`

- Negative, if `wstr1 < wstr2`

**Related Topics**

- OCIWideCharStrcmp()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.22 OCIWideCharStrncpy()

Copies, at most, n characters of a wide-character string into the destination array.

#### Purpose

Copies, at most, n characters from a wide-character string into a destination.

#### Syntax

    size_t OCIWideCharStrncpy ( void             *hndl,
                                OCIWchar         *wdststr,
                                const OCIWchar   *wsrcstr,
                                size_t            n );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wdststr (OUT)
Pointer to the destination `wchar` buffer.

wsrcstr (IN)
Pointer to the source `wchar` string.

n (IN)
Number of characters from `wsrcstr` to copy.

#### Comments

This function is similar to `OCIWideCharStrcpy()`, except that, at most, n characters are copied from the array pointed to by `wsrcstr` to the array pointed to by `wdststr`. Note that the `NULL` terminator in `wdststr` stops copying, and the result string is `NULL`-terminated. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The number of characters copied, not including the `NULL` terminator.

**Related Topics**

- OCIWideCharStrcpy()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.23 OCIWideCharStrrchr()

Searches for the last occurrence of a character in a wide-character string.

#### Purpose

Searches for the last occurrence of a character in a wide-character string.

#### Syntax

    OCIWchar *OCIWideCharStrrchr ( void              *hndl,
                                   const OCIWchar    *wstr,
                                   OCIWchar           wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wstr (IN)
Pointer to the `wchar` string to search in.

wc (IN)
The `wchar` to search for.

#### Comments

Searches for the last occurrence of `wc` in the `wchar` string pointed to by `wstr`. If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

The `wchar` pointer if successful; otherwise, a `NULL` pointer.

**Related Topics**

- OCIWideCharStrchr()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.24 OCIWideCharToLower()

Converts a specified wide character into the corresponding lowercase character.

#### Purpose

Converts the wide-character string specified by `wc` into the corresponding lowercase character, if it exists, in the specified locale. If no corresponding lowercase character exists, then it returns `wc` itself.

#### Syntax

    OCIWchar OCIWideCharToLower ( void        *hndl,
                                  OCIWchar     wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for lowercase conversion.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

A `wchar`.

**Related Topics**

- OCIWideCharToUpper()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.25 OCIWideCharToMultiByte()

Converts a `NULL`-terminated wide-character string into a multibyte string.

#### Purpose

Converts an entire `NULL`-terminated wide-character string into a multibyte string.

#### Syntax

    sword OCIWideCharToMultiByte ( void             *hndl,
                                   OraText          *dst,
                                   const OCIWchar   *src,
                                   size_t           *rsize );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set of the string.

dst (OUT)
Destination buffer for a multibyte string. The output buffer is `NULL`-terminated.

src (IN)
Source `wchar` string to be converted.

rsize (OUT)
Number of bytes written into destination buffer. If it is a `NULL` pointer, then nothing is returned.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIMultiByteToWideChar()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.4.26 OCIWideCharToUpper()

Converts a specified wide character into the corresponding uppercase character.

#### Purpose

Converts the wide-character string specified by `wc` into the corresponding uppercase character, if it exists, in the specified locale. If no corresponding uppercase character exists, then it returns `wc` itself.

#### Syntax

    OCIWchar OCIWideCharToUpper ( void      *hndl,
                                  OCIWchar   wc );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle to determine the character set.

wc (IN)
The `wchar` for uppercase conversion.

#### Comments

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

A `wchar`.

**Related Topics**

- OCIWideCharToLower()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
