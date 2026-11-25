Lists and describes OCI Locale Functions.

Table 31-2 lists the OCI locale functions that are described in this section.

An Oracle locale consists of language, territory, and character set definitions. The locale determines conventions such as day and month names, and date, time, number, and currency formats. A globalized application obeys a user's locale setting and cultural conventions. For example, when the locale is set to German, users expect to see day and month names in German.

Table 31-2 OCI Locale Functions  

| Function                       | Purpose                                                                                                                                           |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| OCINlsCharSetIdToName()        | Return the Oracle Database character set name from the specified character set ID                                                                 |
| OCINlsCharSetNameToId()        | Return the Oracle Database character set ID for the specified Oracle Database character set name                                                  |
| OCINlsEnvironmentVariableGet() | Return the character set ID from `NLS_LANG` or the national character set ID from `NLS_NCHAR`                                                     |
| OCINlsGetInfo()                | Copy locale information from an OCI environment or user session handle into an array pointed to by the destination buffer within a specified size |
| OCINlsNumericInfoGet()         | Copy numeric language information from the OCI environment or user session handle into an output number variable                                  |

### 31.2.1 OCINlsCharSetIdToName()

Returns the Oracle Database character set name from the specified character set ID.

#### Purpose

Returns the Oracle Database character set name from the specified character set ID.

#### Syntax

    sword OCINlsCharSetIdToName ( void      *hndl,
                                  OraText   *buf,
                                  size_t     buflen
                                  ub2        id );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle. If the handle is invalid, then the function returns `OCI_INVALID_HANDLE`.

buf (OUT)
Points to the destination buffer. If the function returns `OCI_SUCCESS`, then the parameter contains a `NULL`-terminated string for the character set name.

buflen (IN)
The size of the destination buffer. The recommended size is `OCI_NLS_MAXBUFSZ `to guarantee storage for an Oracle Database character set name. If the size of the destination buffer is smaller than the length of the character set name, then the function returns `OCI_ERROR`.

id (IN)
Oracle Database character set ID.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

### 31.2.2 OCINlsCharSetNameToId()

Returns the Oracle Database character set ID for the specified Oracle Database character set name.

#### Purpose

Returns the Oracle Database character set ID for the specified Oracle Database character set name.

#### Syntax

    ub2 OCINlsCharSetNameToId ( void            *hndl,
                                const OraText   *name );

#### Parameters

hndl (IN/OUT)
OCI environment or user session handle. If the handle is invalid, then the function returns zero.

name (IN)
Pointer to a `NULL`-terminated Oracle Database character set name. If the character set name is invalid, then the function returns zero.

#### Returns

Character set ID if the specified character set name and the OCI handle are valid. Otherwise, it returns `0`.

### 31.2.3 OCINlsEnvironmentVariableGet()

Returns the character set ID from `NLS_LANG` or the national character set ID from `NLS_NCHAR`.

#### Purpose

Returns the character set ID from `NLS_LANG` or the national character set ID from `NLS_NCHAR`.

#### Syntax

    sword OCINlsEnvironmentVariableGet ( void       *val,
                                         size_t      size,
                                         ub2         item,
                                         ub2         charset,
                                         size_t     *rsize );

#### Parameters

val (IN/OUT)
Returns a value of a globalization support environment variable, such as the `NLS_LANG` character set ID or the `NLS_NCHAR` character set ID.

size (IN)
Specifies the size of the given output value, which is applicable only to string data. The maximum length for each piece of information is` ``OCI_NLS_MAXBUFSZ` bytes. For numeric data, this argument is ignored.

item (IN)
Specifies one of these values to get from the globalization support environment variable:

- `OCI_NLS_CHARSET_ID`: `NLS_LANG` character set ID in `ub2` data type; if `NLS_LANG` is not set, the default character set ID is returned (ASCII).

- `OCI_NLS_NCHARSET_ID`: `NLS_NCHAR` character set ID in `ub2` data type; if `NLS_NCHAR` is not set, the value of `OCI_NLS_CHARSET_ID` is returned instead.

<!-- -->

charset (IN)
Specifies the character set ID for retrieved string data. If it is `0`, then the `NLS_LANG` value is used. `OCI_UTF16ID` is a valid value for this argument. For numeric data, this argument is ignored.

rsize (OUT)
The length of the return value in bytes.

#### Comments

To allow for future enhancements of this function (to retrieve other values from environment variables) the data type of the output `val` is a pointer to `void`. String data is not terminated by `NULL`.

Note that the function does not take an environment handle, so the character set ID and the national character set ID that it returns are the values specified in `NLS_LANG` and `NLS_NCHAR`, instead of the values saved in the OCI environment handle. To get the character set IDs used by the OCI environment handle, call `OCIAttrGet()` for `OCI_ATTR_ENV_CHARSET_ID` and `OCI_ATTR_ENV_NCHARSET_ID`, respectively.

#### Returns

`OCI_SUCCESS`; or `OCI_ERROR`.

**Related Topics**

- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)

### 31.2.4 OCINlsGetInfo()

Copy locale information from an OCI environment or user session handle into an array pointed to by the destination buffer within a specified size.

#### Purpose

Obtains locale information from an OCI environment or user session handle to an array pointed to by the destination buffer within a specified size.

#### Syntax

    sword OCINlsGetInfo ( void        *hndl,
                          OCIError    *errhp,
                          OraText     *buf,
                          size_t       buflen,
                          ub2          item );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle initialized in object mode.

errhp (IN/OUT)
The OCI error handle. If there is an error, then it is recorded in `errhp`, and the function returns a `NULL` pointer. Diagnostic information can be obtained by calling `OCIErrorGet()`.

buf (OUT)
Pointer to the destination buffer. Returned strings are terminated by a `NULL` character.

buflen (IN)
The size of the destination buffer. The maximum length for each piece of information is `OCI_NLS_MAXBUFSZ` bytes.

`OCI_NLS_MAXBUFSIZE`: When calling `OCINlsGetInfo`(), you must allocate the buffer to store the returned information. The buffer size depends on which item you are querying and what encoding you are using to store the information. Developers should not need to know how many bytes it takes to store `January` in Japanese using JA16SJIS encoding. The `OCI_NLS_MAXBUFSZ` attribute guarantees that the buffer is big enough to hold the largest item returned by `OCINlsGetInfo`().

item (IN)
Specifies which item in the OCI environment handle to return. It can be one of these values:

- `OCI_NLS_DAYNAME1`: Native name for Monday
- `OCI_NLS_DAYNAME2`: Native name for Tuesday
- `OCI_NLS_DAYNAME3`: Native name for Wednesday
- `OCI_NLS_DAYNAME4`: Native name for Thursday
- `OCI_NLS_DAYNAME5`: Native name for Friday
- `OCI_NLS_DAYNAME6`: Native name for Saturday
- `OCI_NLS_DAYNAME7`: Native name for Sunday
- `OCI_NLS_ABDAYNAME1`: Native abbreviated name for Monday
- `OCI_NLS_ABDAYNAME2`: Native abbreviated name for Tuesday
- `OCI_NLS_ABDAYNAME3`: Native abbreviated name for Wednesday
- `OCI_NLS_ABDAYNAME4`: Native abbreviated name for Thursday
- `OCI_NLS_ABDAYNAME5`: Native abbreviated name for Friday
- `OCI_NLS_ABDAYNAME6`: Native abbreviated name for Saturday
- `OCI_NLS_ABDAYNAME7`: Native abbreviated name for Sunday
- `OCI_NLS_MONTHNAME1`: Native name for January
- `OCI_NLS_MONTHNAME2`: Native name for February
- `OCI_NLS_MONTHNAME3`: Native name for March
- `OCI_NLS_MONTHNAME4`: Native name for April
- `OCI_NLS_MONTHNAME5`: Native name for May
- `OCI_NLS_MONTHNAME6`: Native name for June
- `OCI_NLS_MONTHNAME7`: Native name for July
- `OCI_NLS_MONTHNAME8`: Native name for August
- `OCI_NLS_MONTHNAME9`: Native name for September
- `OCI_NLS_MONTHNAME10`: Native name for October
- `OCI_NLS_MONTHNAME11`: Native name for November
- `OCI_NLS_MONTHNAME12`: Native name for December
- `OCI_NLS_ABMONTHNAME1`: Native abbreviated name for January
- `OCI_NLS_ABMONTHNAME2`: Native abbreviated name for February
- `OCI_NLS_ABMONTHNAME3`: Native abbreviated name for March
- `OCI_NLS_ABMONTHNAME4`: Native abbreviated name for April
- `OCI_NLS_ABMONTHNAME5`: Native abbreviated name for May
- `OCI_NLS_ABMONTHNAME6`: Native abbreviated name for June
- `OCI_NLS_ABMONTHNAME7`: Native abbreviated name for July
- `OCI_NLS_ABMONTHNAME8`: Native abbreviated name for August
- `OCI_NLS_ABMONTHNAME9`: Native abbreviated name for September
- `OCI_NLS_ABMONTHNAME10`: Native abbreviated name for October
- `OCI_NLS_ABMONTHNAME11`: Native abbreviated name for November
- `OCI_NLS_ABMONTHNAME12`: Native abbreviated name for December
- `OCI_NLS_YES`: Native string for affirmative response
- `OCI_NLS_NO`: Native negative response
- `OCI_NLS_AM`: Native equivalent string of AM
- `OCI_NLS_PM`: Native equivalent string of PM
- `OCI_NLS_AD`: Native equivalent string of AD
- `OCI_NLS_BC`: Native equivalent string of BC
- `OCI_NLS_DECIMAL`: Decimal character
- `OCI_NLS_GROUP`: Group separator
- `OCI_NLS_DEBIT`: Native symbol of debit
- `OCI_NLS_CREDIT`: Native symbol of credit
- `OCI_NLS_DATEFORMAT`: Oracle Database date format
- `OCI_NLS_INT_CURRENCY`: International currency symbol
- `OCI_NLS_DUAL_CURRENCY`: Dual currency symbol
- `OCI_NLS_LOC_CURRENCY`: Locale currency symbol
- `OCI_NLS_LANGUAGE`: Language name
- `OCI_NLS_ABLANGUAGE`: Abbreviation for language name
- `OCI_NLS_TERRITORY`: Territory name
- `OCI_NLS_CHARACTER_SET`: Character set name
- `OCI_NLS_LINGUISTIC_NAME`: Linguistic sort name
- `OCI_NLS_CALENDAR`: Calendar name
- `OCI_NLS_WRITING_DIR`: Language writing direction
- `OCI_NLS_ABTERRITORY`: Territory abbreviation
- `OCI_NLS_DDATEFORMAT`: Oracle Database default date format
- `OCI_NLS_DTIMEFORMAT`: Oracle Database default time format
- `OCI_NLS_SFDATEFORMAT`: Local date format
- `OCI_NLS_SFTIMEFORMAT`: Local time format
- `OCI_NLS_NUMGROUPING`: Number grouping fields
- `OCI_NLS_LISTSEP`: List separator
- `OCI_NLS_MONDECIMAL`: Monetary decimal character
- `OCI_NLS_MONGROUP`: Monetary group separator
- `OCI_NLS_MONGROUPING`: Monetary grouping fields
- `OCI_NLS_INT_CURRENCYSEP`: International currency separator

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 31.2.5 OCINlsNumericInfoGet()

Copy numeric language information from the OCI environment or user session handle into an output number variable.

#### Purpose

Obtains numeric language information from the OCI environment or user session handle and puts it into an output number variable.

#### Syntax

    sword OCINlsNumericInfoGet ( void        *hndl,
                                 OCIError    *errhp,
                                 sb4         *val,
                                 ub2          item );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle. If the handle is invalid, it returns `OCI_INVALID_HANDLE`.

errhp (IN/OUT)
The OCI error handle. If there is an error, then it is recorded in `errhp`, and the function returns a `NULL` pointer. Diagnostic information can be obtained by calling `OCIErrorGet()`.

val (OUT)
Pointer to the output number variable. If the function returns `OCI_SUCCESS`, then the parameter contains the requested globalization support numeric information.

item (IN)
It specifies which item to get from the OCI environment handle and can be one of following values:

- `OCI_NLS_CHARSET_MAXBYTESZ`: Maximum character byte size for OCI environment or session handle character set

- `OCI_NLS_CHARSET_FIXEDWIDTH`: Character byte size for fixed-width character set; `0` for variable-width character set

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
