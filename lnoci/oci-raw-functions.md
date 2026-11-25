Lists and describes the OCI raw functions.

Table 28-14 describes the OCI raw functions that are described in this section.

Table 28-14 Raw Functions

| Function            | Purpose                                   |
|:--------------------|:------------------------------------------|
| OCIRawAllocSize()   | Get allocated size of raw memory in bytes |
| OCIRawAssignBytes() | Assign raw bytes to raw                   |
| OCIRawAssignRaw()   | Assign raw to raw                         |
| OCIRawPtr()         | Get raw data pointer                      |
| OCIRawResize()      | Resize memory of variable-length raw      |
| OCIRawSize()        | Get raw size                              |

### 28.5.1 OCIRawAllocSize()

Gets the allocated size of raw memory in bytes.

#### Purpose

Gets the allocated size of raw memory in bytes.

#### Syntax

    sword OCIRawAllocSize ( OCIEnv             *env,
                            OCIError           *err,
                            const OCIRaw       *raw,
                            ub4                *allocsize );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

raw (IN)
Raw data whose allocated size in bytes is returned. This must be a non-`NULL` pointer.

allocsize (OUT)
The allocated size of raw memory in bytes that is returned.

#### Comments

The allocated size is greater than or equal to the actual raw size.

**Related Topics**

- OCIRawResize()
- OCIRawSize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.5.2 OCIRawAssignBytes()

Assigns raw bytes of type `ub1* `to Oracle `OCIRaw* `data type.

#### Purpose

Assigns raw bytes of type `ub1* `to Oracle `OCIRaw* `data type.

#### Syntax

    sword OCIRawAssignBytes ( OCIEnv             *env,
                              OCIError           *err,
                              const ub1          *rhs,
                              ub4                 rhs_len,
                              OCIRaw            **lhs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rhs (IN)
Right-hand side (source) of the assignment, of data type `ub1`.

rhs_len (IN)
Length of the `rhs` raw bytes.

lhs (IN/OUT)
Left-hand side (target) of the assignment `OCIRaw` data.

#### Comments

Assigns `rhs` raw bytes to `lhs` raw data type. The `lhs` raw may be resized depending upon the size of the `rhs`. The raw bytes assigned are of type `ub1`.

**Related Topics**

- OCIRawAssignRaw()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.5.3 OCIRawAssignRaw()

Assigns one Oracle `RAW` data type to another Oracle `RAW` data type.

#### Purpose

Assigns one Oracle `RAW` data type to another Oracle `RAW` data type.

#### Syntax

    sword OCIRawAssignRaw ( OCIEnv             *env,
                            OCIError           *err,
                            const OCIRaw       *rhs,
                            OCIRaw            **lhs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rhs (IN)
Right-hand side (`rhs`) (source) of the assignment; `OCIRaw` data.

lhs (IN/OUT)
Left-hand side (`lhs`) (target) of the assignment; `OCIRaw` data.

#### Comments

Assigns `rhs` `OCIRaw` to `lhs` `OCIRaw`. The `lhs` `OCIRaw` may be resized depending upon the size of the `rhs`.

**Related Topics**

- OCIRawAssignBytes()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.5.4 OCIRawPtr()

Gets the pointer to raw data.

#### Purpose

Gets the pointer to raw data.

#### Syntax

    ub1 *OCIRawPtr ( OCIEnv             *env,
                     const OCIRaw       *raw );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

raw (IN)
Pointer to the data of a given `raw`.

#### Comments

None.

**Related Topics**

- OCIRawAssignBytes()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.5.5 OCIRawResize()

Resizes the memory of a given variable-length `raw`.

#### Purpose

Resizes the memory of a given variable-length `raw`.

#### Syntax

    sword OCIRawResize ( OCIEnv          *env,
                         OCIError        *err,
                         ub2              new_size,
                         OCIRaw         **raw );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

new_size (IN)
New size of the raw data in bytes.

raw (IN)
Variable-length `raw` pointer; the `raw` is resized to `new_size`.

#### Comments

This function resizes the memory of the given variable-length raw in the object cache. The previous contents of the raw are not preserved. This function may allocate the raw in a new memory region in which case the original memory occupied by the given raw is freed. If the input raw is `NULL` (`raw` == `NULL`), then this function allocates memory for the raw data.

If the `new_size` is 0, then this function frees the memory occupied by `raw`, and a `NULL` pointer value is returned.

**Related Topics**

- OCIRawAllocSize()
- OCIRawSize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.5.6 OCIRawSize()

Returns the size of a given raw in bytes.

#### Purpose

Returns the size of a given raw in bytes.

#### Syntax

    ub4 OCIRawSize ( OCIEnv             *env,
                     const OCIRaw       *raw );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

raw (IN/OUT)
Raw whose size is returned.

#### Comments

None.

**Related Topics**

- OCIRawAllocSize()
- OCIRawResize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
