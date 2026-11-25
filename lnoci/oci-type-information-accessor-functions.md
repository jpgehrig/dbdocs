Lists and describes the OCI type information accessor functions.

Table 27-11 describes the OCI type information accessor functions that are described in this section.

Table 27-11 Type Information Accessor Functions

| Function                 | Purpose                                                                                   |
|:-------------------------|:------------------------------------------------------------------------------------------|
| OCITypeArrayByName()     | Get an array of TDOs when given an array of object names                                  |
| OCITypeArrayByFullName() | Get an array of TDOs when given an array of names for schema level or package level types |
| OCITypeArrayByRef()      | Get an array of TDOs when given an array of object references                             |
| OCITypeByFullName()      | Get a TDO when given a name for a schema level or package level type                      |
| OCITypeByName()          | Get a TDO when given an object name                                                       |
| OCITypeByRef()           | Get a TDO when given an object reference                                                  |
| OCITypePackage()         | Get the package name of a type if it is a package type                                    |

### 27.7.1 OCITypeArrayByName()

Gets an array of TDOs when given an array of names.

#### Purpose

Gets an array of TDOs when given an array of names.

**Note:**

`OCITypeArrayByName()` does not support package level types.

#### Syntax

    sword OCITypeArrayByName ( OCIEnv             *envhp,
                               OCIError           *errhp,
                               const OCISvcCtx    *svc,
                               ub4                 array_len,
                               const OraText      *schema_name[],
                               ub4                 s_length[],
                               const OraText      *type_name[],
                               ub4                 t_length[],
                               const OraText      *version_name[],
                               ub4                 v_length[],
                               OCIDuration         pin_duration,
                               OCITypeGetOpt       get_option,
                               OCIType            *tdo[] );

#### Parameters

envhp (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service handle.

array_len (IN)
Number of `schema_name` or `type_name` or `version_name` entries to be retrieved.

schema_name (IN, optional)
Array of schema names associated with the types to be retrieved. The array must have `array_len` elements if specified. If 0 is supplied, the default schema is assumed; otherwise, `schema_name` must have `array_len` number of elements. Zero (0) can be supplied for one or more of the entries to indicate that the default schema is desired for those entries.

s_length (IN)
Array of `schema_name` lengths with each entry corresponding to the length of the corresponding `schema_name` entry in the `schema_name` array in bytes. The array must either have `array_len` number of elements or it must be 0 if `schema_name` is not specified.

type_name (IN)
Array of the names of the types to retrieve. This must have `array_len` number of elements.

t_length (IN)
Array of the lengths of type names in the `type_name` array in bytes.

version_name (IN)
The version name is ignored and the latest version of the requested type is returned. Because type evolution was available starting in release 9.0, pre-9.0 applications attempting to access an altered type generate an error. These applications must be modified, recompiled, and relinked using the latest type definition.

Array of the version names of the types to retrieve corresponding. This can be 0 to indicate retrieval of the most current versions, or it must have `array_len` number of elements.

If 0 is supplied, the most current version is assumed, otherwise it must have `array_len` number of elements. Zero (0) can be supplied for one or more of the entries to indicate that the current version is desired for those entries.

v_length (IN)
Array of the lengths of version names in the `version_name` array in bytes.

pin_duration (IN)
Pin duration (for example, until the end of the current transaction) for the types retrieved. See `oro.h` for a description of each option.

get_option (IN)
Option for loading the types. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Output array for the pointers to each pinned type in the object cache. It must have space for `array_len` pointers. Use `OCIObjectGetObjectRef()` to obtain the CREF to each pinned type descriptor.

#### Comments

Gets pointers to the existing types associated with the schema or type name array.

You can use the `get_option` parameter to control the portion of the TDO that gets loaded for each round-trip.

This function returns an error if any of the required parameters is `NULL` or any object types associated with a schema or type name entry do not exist.

To retrieve a single type, rather than an array, use `OCITypeByName()`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeArrayByRef()
- OCITypeByName()
- OCITypeByRef()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectGetObjectRef()](oci-miscellaneous-object-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.2 OCITypeArrayByFullName()

Gets the most current version of an existing array of TDOs when given an array of names for schema level or package level types.

#### Purpose

Gets the most current version of an existing array of TDOs when given an array of names for schema level or package level types.

**Note:**

`OCITypeArrayByFullName()` is the array version of `OCITypeByFullName()`. This means that these two functions are functionally identical and one implements `OCITypeArrayByFullName()` using `OCITypeByName()` and vice versa.

#### Syntax

    sword OCITypeArrayByFullName( OCIEnv          *env,
                                  OCIError        *err,
                                  const OCISvcCtx *svc,
                                  ub4              array_len,
                                  const oratext   *full_type_name[],
                                  ub4              f_t_length[],
                                  const oratext   *version_name[],
                                  ub4              v_length[],
                                  OCIDuration      pin_duration,
                                  OCITypeGetOpt    get_option,
                                  OCIType         *tdo[])

#### Parameters

envhp (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service handle.

array_len (IN)
Number of `schema_name` or `type_name` or `version_name` entries to be retrieved.

full_type_name (IN)
The name of the type. If the `full_type_name` is not fully qualified, name resolution will determine the type inferred. For example, `SCOTT.MYPACK.MYTYPE` would refer to type `MYTYPE` in package `MYPACK`. If the current schema is `SCOTT`, this could also be `MYPACK.MYTYPE`. See [Oracle Database PL/SQL Language Reference](../lnpls/plsql-name-resolution.md) for more information about PL/SQL name resolution.

This also applies for schema level types. The string could be `SCOTT.MYTYPE` or simply `MYTYPE` to specify a schema level type.

f_t_length (IN)
Length of `full_type_name` in bytes.

version_name (IN)
The version name is ignored and the latest version of the requested type is returned. Because type evolution was available starting in release 9.0, pre-9.0 applications attempting to access an altered type generate an error. These applications must be modified, recompiled, and relinked using the latest type definition.

Array of the version names of the types to retrieve corresponding. This can be 0 to indicate retrieval of the most current versions, or it must have `array_len` number of elements.

If 0 is supplied, the most current version is assumed, otherwise it must have `array_len` number of elements. Zero (0) can be supplied for one or more of the entries to indicate that the current version is desired for those entries.

v_length (IN)
Array of the lengths of version names in the `version_name` array in bytes.

pin_duration (IN)
Pin duration (for example, until the end of the current transaction) for the types retrieved. See `oro.h` for a description of each option.

get_option (IN)
Option for loading the types. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Output array for the pointers to each pinned type in the object cache. It must have space for `array_len` pointers. Use `OCIObjectGetObjectRef()` to obtain the CREF to each pinned type descriptor.

#### Comments

Gets pointers to the existing types associated with the schema or package type name array.

You can use the `get_option` parameter to control the portion of the TDO that gets loaded for each round-trip.

This function returns an error if any of the required parameters is `NULL` or any object types associated with a schema or package type name entry do not exist.

To retrieve a single type, rather than an array, use `OCITypeByFullName()`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeArrayByRef()
- OCITypeByFullName()
- OCITypeByRef()
- OCITypePackage()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectGetObjectRef()](oci-miscellaneous-object-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.3 OCITypeArrayByRef()

Gets an array of TDOs when given an array of references.

#### Purpose

Gets an array of TDOs when given an array of references.

#### Syntax

    sword OCITypeArrayByRef ( OCIEnv           *envhp,
                              OCIError         *errhp,
                              ub4               array_len,
                              const OCIRef     *type_ref[],
                              OCIDuration       pin_duration,
                              OCITypeGetOpt     get_option,
                              OCIType          *tdo[] );

#### Parameters

envhp (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

array_len (IN)
Number of `schema_name` or `type_name` or `version_name` entries to be retrieved.

type_ref (IN)
Array of `OCIRef *` pointing to the particular version of the type descriptor object to obtain. The array must have `array_len` elements if specified.

pin_duration (IN)
Pin duration (for example, until the end of the current transaction) for the types retrieved. See `oro.h` for a description of each option.

get_option (IN)
Option for loading the types. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Output array for the pointers to each pinned type in the object cache. It must have space for `array_len` pointers. Use `OCIObjectGetObjectRef()` to obtain the CREF to each pinned type descriptor.

#### Comments

Gets pointers to the existing types with the schema or type name array.

This function returns an error if:

- Any of the required parameters is `NULL`

- One or more object types associated with a schema or type name entry does not exist

To retrieve a single type, rather than an array of types, use `OCITypeByRef()`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeArrayByName()
- OCITypeByRef()
- OCITypeByName()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectGetObjectRef()](oci-miscellaneous-object-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.4 OCITypeByFullName()

Gets the most current version of an existing TDO when given a name for a schema level or package level type.

#### Purpose

Gets the most current version of an existing TDO when given a name for a schema level or package level type.

#### Syntax

    sword OCITypeByFullName(OCIEnv          *env,
                            OCIError        *err,
                            const OCISvcCtx *svc,
                            const oratext   *full_type_name,
                            ub4              f_t_length,
                            const oratext   *version_name,
                            ub4              v_length,
                            OCIDuration      pin_duration,
                            OCITypeGetOpt    get_option,
                            OCIType        **tdo);

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service handle.

full_type_name (IN)
The name of the type. If the `full_type_name` is not fully qualified, name resolution will determine the type inferred. Thus, the full path name to the object can include the schema, package name, and type name. For example, `SCOTT.MYPACK.MYTYPE` would refer to type `MYTYPE` in package `MYPACK`. If the current schema is `SCOTT`, this could also be `MYPACK.MYTYPE`. See [Oracle Database PL/SQL Language Reference](../lnpls/plsql-name-resolution.md) for more information about PL/SQL name resolution.

This also applies for schema level types. The string could be `SCOTT.MYTYPE` or simply `MYTYPE` to specify a schema level type.

f_t_length (IN)
Length of `full_type_name` in bytes.

version_name (IN)
The version name is ignored and the latest version of the requested type is returned. Because type evolution was available starting in release 9.0, pre-9.0 applications attempting to access an altered type generate an error. These applications must be modified, recompiled, and relinked using the latest type definition.

User-readable version of the type. Pass as `(text *)0` to retrieve the most current version.

v_length (IN)
Length of `version_name` in bytes.

pin_duration (IN)
Pin duration.

**See Also:**

[Object Duration](object-advanced-topics-in-oci.md)

<!-- -->

get_option ((IN)
Option for loading the types. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Pointer to the pinned type in the object cache.

#### Comments

The fact that the type name is passed as a single string also enables other clients and drivers, such as thick-client JDBC, to easily resolve type names contained in a single name string.

Package types which contain remote package type fields will not be supported by `OCITypeByFullName()`. Any attempt to get a package type, which contains a remote package type field, results in an error.

This function gets a pointer to the existing type associated with the schema or package type name. It returns an error if any of the required parameters is `NULL`, or if the object type associated with the schema or package type name does not exist, or if `version_name` does not exist.

**Note:**

Schema and package type names are case-sensitive. If they have been created with SQL, you must use strings in all uppercase, or the program stops.

This function always makes a round-trip to the server. Therefore calling this function repeatedly to get the type can significantly reduce performance. To minimize the round-trips, the application can call the function for each type and cache the type objects.

To free the type obtained by this function, call `OCIObjectUnpin()` or `OCIObjectPinCountReset()`.

An application can retrieve an array of TDOs by calling `OCITypeArrayByName()` or `OCITypeArrayByRef()`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeByRef()
- OCITypeArrayByFullName()
- OCITypeArrayByRef()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectUnpin()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectPinCountReset()](oci-pin-unpin-and-free-functions.md)
- OCITypeArrayByName()
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.5 OCITypeByName()

Gets the most current version of an existing TDO.

#### Purpose

Gets the most current version of an existing TDO. This call does not support package level types. The name of the schema and the name of the type are each entered in separate strings.

#### Syntax

    sword OCITypeByName ( OCIEnv               *env,
                          OCIError             *err,
                          const OCISvcCtx      *svc,
                          const OraText        *schema_name,
                          ub4                   s_length,
                          const OraText        *type_name,
                          ub4                   t_length,
                          const OraText        *version_name,
                          ub4                   v_length,
                          OCIDuration           pin_duration,
                          OCITypeGetOpt         get_option
                          OCIType             **tdo );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service handle.

schema_name (IN, optional)
Name of schema associated with the type. By default, the user's schema name is used. This string must be all uppercase, or OCI throws an internal error and the program stops.

s_length (IN)
Length of the `schema_name `parameter, in bytes.

type_name (IN)
Name of the type to get. This string must be all uppercase, or OCI throws an internal error and the program stops.

t_length (IN)
Length of the `type_name `parameter, in bytes.

version_name (IN)
The version name is ignored and the latest version of the requested type is returned. Because type evolution was available starting in release 9.0, pre-9.0 applications attempting to access an altered type generate an error. These applications must be modified, recompiled, and relinked using the latest type definition.

User-readable version of the type. Pass as `(text *)0` to retrieve the most current version.

v_length (IN)
Length of `version_name` in bytes.

pin_duration (IN)
Pin duration.

**See Also:**

[Object Duration](object-advanced-topics-in-oci.md)

<!-- -->

get_option ((IN)
Option for loading the types. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Pointer to the pinned type in the object cache.

#### Comments

This function gets a pointer to the existing type associated with the schema or type name. It returns an error if any of the required parameters is `NULL`, or if the object type associated with the schema or type name does not exist, or if `version_name` does not exist.

**Note:**

Schema and type names are case-sensitive. If they have been created with SQL, you must use strings in all uppercase, or the program stops.

This function always makes a round-trip to the server. Therefore calling this function repeatedly to get the type can significantly reduce performance. To minimize the round-trips, the application can call the function for each type and cache the type objects.

To free the type obtained by this function, call `OCIObjectUnpin()` or `OCIObjectPinCountReset()`.

An application can retrieve an array of TDOs by calling `OCITypeArrayByName()` or `OCITypeArrayByRef()`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeByRef()
- OCITypeArrayByName()
- OCITypeArrayByRef()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectUnpin()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectPinCountReset()](oci-pin-unpin-and-free-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.6 OCITypeByRef()

Gets a TDO when given a reference.

#### Purpose

Gets a TDO when given a reference.

#### Syntax

    sword OCITypeByRef ( OCIEnv          *env,
                         OCIError        *err,
                         const OCIRef    *type_ref,
                         OCIDuration      pin_duration,
                         OCITypeGetOpt    get_option,
                         OCIType        **tdo );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

type_ref (IN)
An `OCIRef *` pointing to the version of the type descriptor object to obtain.

pin_duration (IN)
Pin duration until the end of the current transaction for the type to retrieve. See `oro.h` for a description of each option.

get_option (IN)
Option for loading the type. It can be one of two values:

- `OCI_TYPEGET_HEADER` (only the header is loaded)

- `OCI_TYPEGET_ALL` (TDO and all ADO and MDOs are loaded)

tdo (OUT)
Pointer to the pinned type in the object cache.

#### Comments

`OCITypeByRef()` returns an error if any of the required parameters is `NULL`.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCITypeByName()
- OCITypeArrayByName()
- OCITypeArrayByRef()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.7.7 OCITypePackage()

Returns the package name of a type if it is a package type.

#### Purpose

Returns the package name of a type if it is a package type.

#### Syntax

    oratext* OCITypePackage( OCIEnv        *env,
                             OCIError      *err,
                             const OCIType *tdo,
                             ub4           *n_length);

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tdo (OUT)
Pointer to the pinned type in the object cache.

n_length
Length of the package name, in bytes.

#### Comments

If the type is not a package type, the return value will be null and `n_length` will be zero.

**Related Topics**

- OCITypeArrayByFullName()
- OCITypeByFullName()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
