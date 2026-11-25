Lists and describes OCI character set conversion functions.

Conversion between Oracle Database character sets and Unicode (16-bit, fixed-width Unicode encoding) is supported. Replacement characters are used if a character has no mapping from Unicode to the Oracle Database character set. Therefore, conversion back to the original character set is not always possible without data loss.

Table 31-6 lists the OCI character set conversion functions.

Table 31-6 OCI Character Set Conversion Functions

| Function                                | Purpose                                                                                                                                                                    |
|:----------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| OCICharSetConversionIsReplacementUsed() | Indicate whether replacement characters were used for characters that could not be converted in the last invocation of `OCINlsCharSetConvert()` or `OCICharSetToUnicode()` |
| OCICharSetToUnicode()                   | Convert a multibyte string to Unicode                                                                                                                                      |
| OCINlsCharSetConvert()                  | Convert a string from one character set to another                                                                                                                         |
| OCIUnicodeToCharSet()                   | Convert a Unicode string into multibyte                                                                                                                                    |

### 31.6.1 OCICharSetConversionIsReplacementUsed()

Indicates whether replacement characters were used for characters that could not be converted in the last invocation of `OCINlsCharSetConvert()` or `OCICharSetToUnicode().`

#### Purpose

Indicates whether the replacement character was used for characters that could not be converted during the last invocation of `OCICharSetToUnicode()` or `OCINlsCharSetConvert()`.

#### Syntax

    boolean OCICharSetConversionIsReplacementUsed ( void *hndl );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle.

#### Comments

Conversion between the Oracle Database character set and Unicode (16-bit, fixed-width Unicode encoding) is supported. Replacement characters are used if there is no mapping for a character from Unicode to the Oracle Database character set. Thus, not every character can make a round-trip conversion to the original character. Data loss occurs with certain characters.

#### Returns

The function returns `TRUE` if the replacement character was used when `OCINlsCharSetConvert()` or `OCICharSetToUnicode()` was last invoked. Otherwise the function returns `FALSE`.

**Related Topics**

- OCINlsCharSetConvert()
- OCICharSetToUnicode()

### 31.6.2 OCICharSetToUnicode()

Converts a multibyte string to Unicode.

#### Purpose

Converts a multibyte string pointed to by `src` to Unicode out to the array pointed to by `dst`.

#### Syntax

    sword OCICharSetToUnicode ( void              *hndl,
                                ub2               *dst,
                                size_t             dstlen,
                                const OraText     *src,
                                size_t             srclen,
                                size_t            *rsize );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle.

dst (OUT)
Pointer to a destination buffer.

dstlen (IN)
The size of the destination buffer in characters.

src (IN)
Pointer to a multibyte source string.

srclen (IN)
The size of the source string in bytes.

rsize (OUT`)`
The number of characters converted. If it is a `NULL` pointer, then nothing is returned.

#### Comments

The conversion stops when it reaches the source limitation or destination limitation. The function returns the number of characters converted into a Unicode string. If `dstlen` is `0`, then the function scans the string, counts the number of characters, and returns the number of characters out to `rsize`, but does not convert the string.

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`, `OCI_INVALID_HANDLE`, or `OCI_ERROR`.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.6.3 OCINlsCharSetConvert()

Converts a string from one character set to another.

#### Purpose

Converts a string pointed to by `src` in the character set specified by `srcid` to the array pointed to by `dst` in the character set specified by `dstid`. The conversion stops when it reaches the data size limitation of either the source or the destination. The function returns the number of bytes converted into the destination buffer.

#### Syntax

    sword OCINlsCharSetConvert ( void          *hndl,
                                 OCIError      *errhp,
                                 ub2            dstid,
                                 void          *dstp,
                                 size_t         dstlen,
                                 ub2            srcid,
                                 const void    *srcp,
                                 size_t         srclen,
                                 size_t        *rsize );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle.

errhp (IN/OUT)
OCI error handle. If there is an error, then it is recorded in `errhp` and the function returns a `NULL` pointer. Diagnostic information can be obtained by calling `OCIErrorGet()`.

dstid (IN)
Character set ID for the destination buffer.

dstp (OUT)
Pointer to the destination buffer.

dstlen (IN)
The maximum size in bytes of the destination buffer.

srcid (IN)
Character set ID for the source buffer.

srcp (IN)
Pointer to the source buffer.

srclen (IN)
The length in bytes of the source buffer.

rsize (OUT)
The number of characters converted. If the pointer is `NULL`, then nothing is returned.

#### Comments

Although either the source or the destination character set ID can be specified as `OCI_UTF16ID`, the length of the original and the converted data is represented in bytes, rather than number of characters. Note that the conversion does not stop when it encounters null data. To get the character set ID from the character set name, use `OCINlsCharSetNameToId()`. To check if derived data in the destination buffer contains replacement characters, use `OCICharSetConversionIsReplacementUsed()`. The buffers should be aligned with the byte boundaries appropriate for the character sets. For example, the `ub2` data type is necessary to hold strings in UTF-16.

#### Returns

`OCI_SUCCESS` or `OCI_ERROR`; number of bytes converted.

**Related Topics**

- [OCINlsCharSetNameToId()](oci-locale-functions.md)
- OCICharSetConversionIsReplacementUsed()
- [OCIErrorGet()](miscellaneous-functions.md)

### 31.6.4 OCIUnicodeToCharSet()

Converts a Unicode string into multibyte string out to an array.

#### Purpose

Converts a Unicode string to a multibyte string out to an array.

#### Syntax

    sword OCIUnicodeToCharSet ( void        *hndl,
                                OraText     *dst,
                                size_t       dstlen,
                                const ub2   *src,
                                size_t       srclen,
                                size_t      *rsize );

#### Parameters

hndl (IN/OUT)
Pointer to an OCI environment or user session handle.

dst (OUT)
Pointer to a destination buffer.

dstlen (IN)
The size of the destination buffer in bytes.

src (IN)
Pointer to a Unicode string.

srclen (IN)
The size of the source string in characters.

rsize (OUT)
The number of bytes converted. If it is a `NULL` pointer, then nothing is returned.

#### Comments

The conversion stops when it reaches the source limitation or destination limitation. The function returns the number of bytes converted into a multibyte string. If `dstlen` is zero, then the function returns the number of bytes out to `rsize` without conversion.

If a Unicode character is not convertible for the character set specified in OCI environment or user session handle, then a replacement character is used. In this case, `OCICharSetConversionIsReplacementUsed()` returns `TRUE`.

If `OCI_UTF16ID` is specified for SQL `CHAR` data in the `OCIEnvNlsCreate()` function, then this function produces an error.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCICharSetConversionIsReplacementUsed()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
