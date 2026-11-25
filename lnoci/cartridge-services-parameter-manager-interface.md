Lists and describes cartridge services parameter manager interface functions.

Table 29-4 lists the parameter manager interface functions that are described in this section.

Table 29-4 Parameter Manager Interface Functions

| Function               | Purpose                                                                               |
|:-----------------------|:--------------------------------------------------------------------------------------|
| OCIExtractFromFile()   | Process the keys and their values in the given file                                   |
| OCIExtractFromList()   | Generate a list of values for the parameter denoted by `index` in the parameter list  |
| OCIExtractFromStr()    | Process the keys and the their values in the given string                             |
| OCIExtractInit()       | Initialize the parameter manager                                                      |
| OCIExtractReset()      | Reinitialize memory                                                                   |
| OCIExtractSetKey()     | Register information about a key with the parameter manager                           |
| OCIExtractSetNumKeys() | Inform the parameter manager of the number of keys that are to be registered          |
| OCIExtractTerm()       | Release all dynamically allocated storage                                             |
| OCIExtractToBool()     | Get the Boolean value for the specified key                                           |
| OCIExtractToInt()      | Get the integer value for the specified key                                           |
| OCIExtractToList()     | Generate a list of parameters from the parameter structures that are stored in memory |
| OCIExtractToOCINum()   | Get the number value for the specified key                                            |
| OCIExtractToStr()      | Get the string value for the specified key                                            |

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-cartridge-services.md) for more information about using these functions

### 29.5.1 OCIExtractFromFile()

Processes the keys and their values in the given file.

#### Purpose

Processes the keys and their values in the given file.

#### Syntax

    sword OCIExtractFromFile( void     *hndl,
                              OCIError *err,
                              ub4       flag,
                              OraText  *filename );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

flag (IN)
Zero or has one or more of the following bits set:

`OCI_EXTRACT_CASE_SENSITIVE`

`OCI_EXTRACT_UNIQUE_ABBREVS`

`OCI_EXTRACT_APPEND_VALUES`

filename (IN)
A `NULL`-terminated file name string.

#### Comments

`OCIExtractSetNumKeys()` and `OCIExtractSetKey()` functions must be called to define all of the keys before this routine is called.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIExtractSetNumKeys()
- OCIExtractSetKey()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.2 OCIExtractFromList()

Generates a list of values for the parameter denoted by index in the parameter list.

#### Purpose

Generates a list of values for the parameter denoted by index in the parameter list.

#### Syntax

    sword OCIExtractFromList( void        *hndl,
                              OCIError    *err,
                              uword        index,
                              OraText    **name,
                              ub1         *type,
                              uword       *numvals,
                              void      ***values );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

index (IN)
Which parameter to retrieve from the parameter list.

name (OUT)
The name of the key for the current parameter.

type (OUT)
Type of the current parameter:

`OCI_EXTRACT_TYPE_STRING`

`OCI_EXTRACT_TYPE_INTEGER`

`OCI_EXTRACT_TYPE_OCINUM`

`OCI_EXTRACT_TYPE_BOOLEAN`

numvals (OUT)
Number of values for this parameter.

values (OUT)
The values for this parameter.

#### Comments

`OCIExtractToList()` must be called prior to calling this routine to generate the parameter list from the parameter structures that are stored in memory.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIExtractToList()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.3 OCIExtractFromStr()

Processes the keys and their values in the given string.

#### Purpose

Processes the keys and their values in the given string.

#### Syntax

    sword OCIExtractFromStr( void     *hndl,
                             OCIError *err,
                             ub4       flag,
                             OraText  *input );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. For diagnostic information call `OCIErrorGet()`.

flag (IN)
Zero or has one or more of the following bits set:

`OCI_EXTRACT_CASE_SENSITIVE`

`OCI_EXTRACT_UNIQUE_ABBREVS`

`OCI_EXTRACT_APPEND_VALUES`

input (IN)
A `NULL`-terminated input string.

#### Comments

`OCIExtractSetNumKeys()` and `OCIExtractSetKey()` functions must be called to define all of the keys before this routine is called.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIExtractSetNumKeys()
- OCIExtractSetKey()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.4 OCIExtractInit()

Initializes the parameter manager.

#### Purpose

Initializes the parameter manager.

#### Syntax

    sword OCIExtractInit( void      *hndl,
                          OCIError  *err);

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

This function must be called before calling any other parameter manager routine, and it must be called only once. The globalization support information is stored inside the parameter manager context and used in subsequent calls to `OCIExtract` functions.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.5 OCIExtractReset()

Frees the memory currently used for parameter storage, key definition storage, and parameter value lists and reinitializes the structure.

#### Purpose

Frees the memory currently used for parameter storage, key definition storage, and parameter value lists and reinitializes the structure.

#### Syntax

    sword OCIExtractReset( void      *hndl,
                           OCIError  *err );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`,

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.6 OCIExtractSetKey()

Registers information about a key with the parameter manager.

#### Purpose

Registers information about a key with the parameter manager.

#### Syntax

    sword OCIExtractSetKey( void        *hndl,
                            OCIError    *err,
                            const text  *name,
                            ub1          type,
                            ub4          flag,
                            const void  *defval,
                            const sb4   *intrange,
                            const text  *strlist );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

name (IN)
The name of the key.

type (IN)
The type of the key:

`OCI_EXTRACT_TYPE_INTEGER`

`OCI_EXTRACT_TYPE_OCINUM`

`OCI_EXTRACT_TYPE_STRING`

`OCI_EXTRACT_TYPE_BOOLEAN`

flag (IN)
Set to `OCI_EXTRACT_MULTIPLE` if the key can take multiple values or 0 otherwise.

defval (IN)
Set to the default value for the key. It can be `NULL` if there is no default. A string default must be a (text\*) type, an integer default must be an (sb4\*) type, and a Boolean default must be a (ub1\*) type.

intrange (IN)
Starting and ending values for the allowable range of integer values; can be `NULL` if the key is not an integer type or if all integer values are acceptable.

strlist (IN)
List of all acceptable text strings for the key ended with 0 (or `NULL`). Can be `NULL` if the key is not a string type or if all text values are acceptable.

#### Comments

This routine must be called after calling `OCIExtractSetNumKeys()` and before calling `OCIExtractFromFile()` or `OCIExtractFromStr()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIExtractSetNumKeys()
- OCIExtractFromFile()
- OCIExtractFromStr()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.7 OCIExtractSetNumKeys()

Informs the parameter manager of the number of keys that are to be registered.

#### Purpose

Informs the parameter manager of the number of keys that are to be registered.

#### Syntax

    sword OCIExtractSetNumKeys( void    *hndl,
                                CIError *err,
                                uword    numkeys );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

numkeys (IN)
The number of keys that are to be registered with `OCIExtractSetKey()`.

#### Comments

This routine must be called prior to the first call of `OCIExtractSetKey()`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- OCIExtractSetKey()
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.8 OCIExtractTerm()

Releases all dynamically allocated storage.

#### Purpose

Releases all dynamically allocated storage.

#### Syntax

    sword OCIExtractTerm( void      *hndl,
                          OCIError  *err );

#### Parameters

hndl (IN/OUT)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

#### Comments

This function may perform other internal bookkeeping functions. It must be called when the parameter manager is no longer being used, and it must be called only once.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.9 OCIExtractToBool()

Gets the Boolean value for the specified key.

#### Purpose

The `valno`'th value (starting with 0) is returned.

#### Syntax

    sword OCIExtractToBool( void      *hndl,
                            OCIError  *err,
                            OraText   *keyname,
                            uword      valno,
                            ub1       *retval );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

keyname (IN)
Key name.

valno (IN)
Which value to get for this key.

retval (OUT)
The actual Boolean value.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; `OCI_NO_DATA`; or `OCI_ERROR`.

`OCI_NO_DATA` means that there is no `valno`'th value for this key.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.10 OCIExtractToInt()

Gets the integer value for the specified key.

#### Purpose

The `valno`'th value (starting with 0) is returned.

#### Syntax

    sword OCIExtractToInt( void      *hndl,
                           OCIError  *err,
                           OraText   *keyname,
                           uword      valno,
                           sb4       *retval );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

keyname (IN)
Keyname (IN).

valno (IN)
Which value to get for this key.

retval (OUT)
The actual integer value.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; `OCI_NO_DATA`; or `OCI_ERROR`.

`OCI_NO_DATA` means that there is no `valno`'th value for this key.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.11 OCIExtractToList()

Generates a list of parameters from the parameter structures that are stored in memory.

#### Purpose

Must be called before `OCIExtractValues()` is called.

#### Syntax

    sword OCIExtractToList( void      *hndl,
                            OCIError  *err,
                            uword     *numkeys );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

numkeys (OUT)
The number of distinct keys stored in memory.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; or `OCI_ERROR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.12 OCIExtractToOCINum()

Gets the OCINumber value for the specified key.

#### Purpose

The `valno`'th value (starting with 0) is returned.

#### Syntax

    sword OCIExtractToOCINum( void      *hndl,
                              OCIError  *err,
                              OraText   *keyname,
                              uword      valno,
                              OCINumber *retval );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

keyname (IN)
Key name.

valno (IN)
Which value to get for this key.

retval (OUT)
The actual OCINumber value.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; `OCI_NO_DATA`; or `OCI_ERROR`.

`OCI_NO_DATA` means that there is no `valno`'th value for this key.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 29.5.13 OCIExtractToStr()

Gets the string value for the specified key.

#### Purpose

The `valno`'th value (starting with 0) is returned.

#### Syntax

    sword OCIExtractToStr( void       *hndl,
                           OCIError   *err,
                           OraText    *keyname,
                           uword       valno,
                           OraText    *retval,
                           uword       buflen );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

keyname (IN)
Key name.

valno (IN)
Which value to get for this key.

retval (OUT)
The actual `NULL`-terminated string value.

buflen
The length of the buffer for `retval`.

#### Returns

`OCI_SUCCESS`; `OCI_INVALID_HANDLE`; `OCI_NO_DATA`; or `OCI_ERROR`.

`OCI_NO_DATA` means that there is no `valno`'th value for this key.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
