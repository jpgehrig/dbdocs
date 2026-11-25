Lists and describes the OCI string functions.

Table 28-16 describes the OCI string functions that are described in this section.

Table 28-16 String Functions

| Function              | Purpose                                          |
|:----------------------|:-------------------------------------------------|
| OCIStringAllocSize()  | Get the allocated size of string memory in bytes |
| OCIStringAssign()     | Assign a string to a string                      |
| OCIStringAssignText() | Assign a text string to a string                 |
| OCIStringPtr()        | Get a string pointer                             |
| OCIStringResize()     | Resize the string memory                         |
| OCIStringSize()       | Get the string size                              |

### 28.7.1 OCIStringAllocSize()

Gets the allocated size of string memory in code points (Unicode) or in bytes.

#### Purpose

Gets the allocated size of string memory in code points (Unicode) or in bytes.

#### Syntax

    sword OCIStringAllocSize ( OCIEnv              *env,
                               OCIError            *err,
                               const OCIString     *vs,
                               ub4                 *allocsize );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

vs (IN)
String whose allocated size in bytes is returned. The `vs` parameter must be a non-`NULL` pointer.

allocsize (OUT)
The allocated size of string memory in bytes is returned.

#### Comments

The allocated size is greater than or equal to the actual string size.

**Related Topics**

- OCIStringResize()
- OCIStringSize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.7.2 OCIStringAssign()

Assigns one string to another string.

#### Purpose

Assigns one string to another string.

#### Syntax

    sword OCIStringAssign ( OCIEnv               *env,
                            OCIError             *err,
                            const OCIString      *rhs,
                            OCIString           **lhs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rhs (IN)
Right-hand side (source) of the assignment. Can be in UTF-16 format.

lhs (IN/OUT)
Left-hand side (target) of the assignment. Its buffer is in UTF-16 format if `rhs` is UTF-16.

#### Comments

Assigns `rhs` string to `lhs` string. The `lhs` string can be resized depending upon the size of the `rhs`. The assigned string is `NULL`-terminated. The length field does not include the extra code point or byte needed for `NULL`-termination.

#### Returns

This function returns an error if the assignment operation runs out of space.

**Related Topics**

- OCIStringAssignText()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.7.3 OCIStringAssignText()

Assigns the source text string to the target string.

#### Purpose

Assigns the source text string to the target string.

#### Syntax

    sword OCIStringAssignText ( OCIEnv           *env,
                                OCIError         *err,
                                const OraText    *rhs,
                                ub4               rhs_len,
                                OCIString       **lhs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rhs (IN)
Right-hand side (source) of the assignment, a text or UTF-16 Unicode string.

rhs_len (IN)
Length of the `rhs` string in bytes.

lhs (IN/OUT)
Left-hand side (target) of the assignment. Its buffer is in Unicode if `rhs` is in Unicode.

#### Comments

Assigns `rhs` string to `lhs` string. The `lhs` string may be resized depending upon the size of the `rhs`. The assigned string is `NULL`-terminated. The length field does not include the extra byte or code point needed for `NULL`-termination.

**Related Topics**

- OCIStringAssign()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.7.4 OCIStringPtr()

Gets a pointer to the text of a given string.

#### Purpose

Gets a pointer to the text of a given string.

#### Syntax

    text *OCIStringPtr ( OCIEnv               *env,
                         const OCIString      *vs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

vs (IN)
Pointer to the `OCIString` object whose character string is returned. If `vs` is in UTF-16 format, the returned buffer is also in UTF-16 format. To determine the encoding of the returned buffer, check the UTF-16 information in the `OCIString` `vs` itself, because it is not guaranteed that a particular `OCIString` will have the same setting as `env` does. Check an object OCI function that is designed to check member fields in objects.

#### Comments

None.

**Related Topics**

- OCIStringAssign()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.7.5 OCIStringResize()

Resizes the memory of a given string.

#### Purpose

Resizes the memory of a given string.

#### Syntax

    sword OCIStringResize ( OCIEnv          *env,
                            OCIError        *err,
                            ub4              new_size,
                            OCIString      **str );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

new_size (IN)
New memory size of the string in bytes. The `new_size` parameter must include space for the `NULL` character as the string terminator.

str (IN/OUT)
Allocated memory for the string that is freed from the OCI object cache.

#### Comments

This function resizes the memory of the given variable-length string in the object cache. Contents of the string are not preserved. This function may allocate the string in a new memory region, in which case the original memory occupied by the given string is freed. If `str` is `NULL`, this function allocates memory for the string. If `new_size` is 0, this function frees the memory occupied by `str` and a `NULL` pointer value is returned.

**Related Topics**

- OCIStringAllocSize()
- OCIStringSize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.7.6 OCIStringSize()

Gets the size of the given string `vs`.

#### Purpose

Gets the size of the given string `vs`.

#### Syntax

    ub4 OCIStringSize ( OCIEnv              *env,
                        const OCIString     *vs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

vs (IN)
String whose size is returned, in number of bytes.

#### Comments

The returned size does not include an extra byte for `NULL` termination.

**Related Topics**

- OCIStringResize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
