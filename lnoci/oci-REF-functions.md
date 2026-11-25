Lists and describes the OCI Reference (`REF`) functions.

Table 28-15 describes the OCI Reference (`REF`) functions that are described in this section.

Table 28-15 Ref Functions

| Function        | Purpose                                            |
|:----------------|:---------------------------------------------------|
| OCIRefAssign()  | Assign one `REF` to another                        |
| OCIRefClear()   | Clear or nullify a `REF`                           |
| OCIRefFromHex() | Convert hexadecimal string to `REF`                |
| OCIRefHexSize() | Return size of hexadecimal representation of `REF` |
| OCIRefIsEqual() | Compare two `REF`s for equality                    |
| OCIRefIsNull()  | Test if a `REF` is `NULL`                          |
| OCIRefToHex()   | Convert `REF` to hexadecimal string                |

### 28.6.1 OCIRefAssign()

Assigns one `REF` to another, such that both reference the same object.

#### Purpose

Assigns one `REF` to another, such that both reference the same object.

#### Syntax

    sword OCIRefAssign ( OCIEnv             *env,
                         OCIError           *err,
                         const OCIRef       *source,
                         OCIRef            **target );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

source (IN)
`REF` to copy from.

target (IN/OUT)
`REF `to copy to.

#### Comments

Copies `source` `REF` to `target REF`; both then reference the same object. If the `target` `REF` pointer is `NULL` (`*target` == `NULL`), then `OCIRefAssign()` allocates memory for the `target REF` in the OCI object cache before the copy operation.

**Related Topics**

- OCIRefIsEqual()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.2 OCIRefClear()

Clears or `NULL`ifies a given `REF`.

#### Purpose

Clears or `NULL`ifies a given `REF`.

#### Syntax

    void OCIRefClear ( OCIEnv        *env,
                       OCIRef        *ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

ref (IN/OUT)
`REF` to clear.

#### Comments

A `REF` is considered to be a `NULL` `REF` if it no longer points to an object. Logically, a `NULL` `REF` is a dangling `REF`.

Note that a `NULL` `REF` is still a valid SQL value and is not SQL `NULL`. It can be used as a valid non-`NULL` constant REF value for a `NOT` `NULL` column or attribute of a row in a table.

If a `NULL` pointer value is passed as a `REF`, then this function is nonoperational.

**Related Topics**

- OCIRefIsNull()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.3 OCIRefFromHex()

Converts the given hexadecimal string into a `REF`.

#### Purpose

Converts the given hexadecimal string into a `REF`.

#### Syntax

    sword OCIRefFromHex ( OCIEnv              *env,
                          OCIError            *err,
                          const OCISvcCtx     *svc,
                          const OraText       *hex,
                          ub4                  length,
                          OCIRef             **ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
The OCI service context handle, if the resulting `ref` is initialized with this service context.

hex (IN)
Hexadecimal text string, previously output by `OCIRefToHex()`, to convert into a `REF`.

length (IN)
Length of the hexadecimal text string.

ref (IN/OUT)
The `REF` into which the hexadecimal string is converted. If `*ref `is `NULL` on input, then space for the `REF` is allocated in the object cache; otherwise, the memory occupied by the given `REF` is reused.

#### Comments

This function ensures that the resulting `REF` is well formed. It does not ensure that the object pointed to by the resulting `REF` exists.

**Related Topics**

- OCIRefToHex()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.4 OCIRefHexSize()

Returns the size of the hexadecimal representation of a `REF`.

#### Purpose

Returns the size of the hexadecimal representation of a `REF`.

#### Syntax

    ub4 OCIRefHexSize ( OCIEnv            *env,
                        const OCIRef      *ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

ref (IN)
`REF` whose size in hexadecimal representation in bytes is returned.

#### Comments

Returns the size of the buffer in bytes required for the hexadecimal representation of the `ref`. A buffer of at least this size must be passed to the ref-to-hex (`OCIRefToHex()`) conversion function.

#### Returns

The size of the hexadecimal representation of the `REF`.

**Related Topics**

- OCIRefFromHex()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.5 OCIRefIsEqual()

Compares two `REF`s to determine if they are equal.

#### Purpose

Compares two `REF`s to determine if they are equal.

#### Syntax

    boolean OCIRefIsEqual ( OCIEnv              *env,
                            const OCIRef        *x,
                            const OCIRef        *y );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

x (IN)
`REF` to compare.

y (IN)
`REF` to compare.

#### Comments

Two `REF`s are equal if and only if they are both referencing the same object, whether persistent or transient.

**Note:**

Two `NULL` `REF`s are considered not equal by this function.

#### Returns

`TRUE`, if the two `REF`s are equal.

`FALSE`, if the two `REF`s are not equal, or `x` is `NULL`, or `y` is `NULL.`

**Related Topics**

- OCIRefAssign()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.6 OCIRefIsNull()

Tests if a `REF` is `NULL`.

#### Purpose

Tests if a `REF` is `NULL`.

#### Syntax

    boolean OCIRefIsNull ( OCIEnv           *env,
                           const OCIRef     *ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

ref (IN)
`REF` to test for `NULL`.

#### Comments

A `REF` is `NULL` if and only if:

- It is supposed to be referencing a persistent object, but the object's identifier is `NULL`

- It is supposed to be referencing a transient object, but it is currently not pointing to an object

  **Note:**

  A `REF` is a dangling REF if the object that it points to does not exist.

#### Returns

Returns `TRUE` if the given `REF` is `NULL`; otherwise, it returns `FALSE`.

**Related Topics**

- OCIRefClear()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.6.7 OCIRefToHex()

Converts a `REF` to a hexadecimal string.

#### Purpose

Converts a `REF` to a hexadecimal string.

#### Syntax

    sword OCIRefToHex ( OCIEnv            *env,
                        OCIError          *err,
                        const OCIRef      *ref,
                        OraText           *hex,
                        ub4               *hex_length );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ref (IN)
`REF` to be converted into a hexadecimal string; if `ref` is a `NULL` `REF` (that is, `OCIRefIsNull`(`ref`) == `TRUE`), then a zero `hex_length` value is returned.

hex (OUT)
Buffer that is large enough to contain the resulting hexadecimal string; the content of the string is opaque to the caller.

hex_length (IN/OUT)
On input, specifies the size of the `hex` buffer; on output, specifies the actual size of the hexadecimal string being returned in `hex`.

#### Comments

Converts the given `REF` into a hexadecimal string, and returns the length of the string. The resulting string is opaque to the caller.

#### Returns

This function returns an error if the given buffer is not big enough to hold the resulting string.

**Related Topics**

- OCIRefFromHex()
- OCIRefHexSize()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
