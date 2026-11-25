Lists and describes cartridge services maintaining context functions.

Table 29-3 lists the maintaining context functions that are described in this section.

Table 29-3 Maintaining Context Functions

| Function                | Purpose                                             |
|:------------------------|:----------------------------------------------------|
| OCIContextClearValue()  | Remove the value stored in the context              |
| OCIContextGenerateKey() | Return a unique 4-byte value each time it is called |
| OCIContextGetValue()    | Return the value stored in the context              |
| OCIContextSetValue()    | Save a value (or address) for a particular duration |

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/cartridge-services-using-C-CPP-and-java.md) for more information about using these functions

### 29.4.1 OCIContextClearValue()

Removes the value that is stored in the context associated with the given key (by calling `OCIContextSetValue()`).

#### Purpose

Removes the value that is stored in the context associated with the given key (by calling `OCIContextSetValue()`).

#### Syntax

    sword OCIContextClearValue( void     *hndl,
                                OCIError *err,
                                ub1      *key,
                                ub1       keylen );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

key (IN)
Unique key value.

keylen (IN)
Length of the key. Maximum value is 255 bytes or `UB1MAXVAL` - 1.

#### Comments

An error is returned when a nonexistent key is passed.

#### Returns

- If the operation succeeds, the function returns `OCI_SUCCESS`.

- If the operation fails, the function returns `OCI_ERROR`.

### 29.4.2 OCIContextGenerateKey()

Returns a unique, 4-byte value each time it is called.

#### Purpose

Returns a unique, 4-byte value each time it is called.

#### Syntax

    sword OCIContextGenerateKey( void     *hndl,
                                 OCIError *err,
                                 ub4      *key );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

key (IN)
Unique key value.

#### Comments

This value is unique for each session.

#### Returns

- If the operation succeeds, the function returns `OCI_SUCCESS`.

- If the operation fails, the function returns `OCI_ERROR`.

### 29.4.3 OCIContextGetValue()

Returns the value that is stored in the context associated with the given key (by calling `OCIContextSetValue()`).

#### Purpose

Returns the value that is stored in the context associated with the given key (by calling `OCIContextSetValue()`).

#### Syntax

    sword OCIContextGetValue( void       *hndl,
                              OCIError   *err,
                              ub1        *key,
                              ub1         keylen,
                              void      **ctx_value );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

key (IN)
Unique key value.

keylen (IN)
Length of the key. Maximum value is 255 bytes or `UB1MAXVAL` - 1.

ctx_value (IN)
Pointer to the value stored in the context (`NULL` if no value was stored).

#### Comments

For `ctx_value`, a pointer to a preallocated pointer for the stored context to be returned is required.

#### Returns

- If the operation succeeds, the function returns `OCI_SUCCESS`.

- If the operation fails, the function returns `OCI_ERROR`.

### 29.4.4 OCIContextSetValue()

Saves a value (or address) for a particular duration.

#### Purpose

Saves a value (or address) for a particular duration.

#### Syntax

    sword OCIContextSetValue( void        *hndl,
                              OCIError    *err,
                              OCIDuration  duration,
                              ub1         *key,
                              ub1          keylen,
                              void        *ctx_value );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

duration (IN)
One of these values (a previously created user duration):

`OCI_DURATION_STATEMENT`

`OCI_DURATION_SESSION`

key (IN)
Unique key value.

keylen (IN)
Length of the key. Maximum value is 255 bytes or `UB1MAXVAL` - 1.

ctx_value (IN)
Pointer that is saved in the context.

#### Comments

The context value being stored must be allocated out of memory of duration greater than or equal to the duration being passed in. The key being passed in should be unique in this session. Trying to save a context value under the same key and duration again results in overwriting the old context value with the new one. Typically, a client allocates a structure, stores its address in the context using this call, and gets this address in a separate call using `OCIContextGetValue()`. The (key, value) association can be explicitly removed by calling `OCIContextClearValue()`, or else it goes away at the end of the duration.

#### Returns

- If the operation succeeds, the function returns `OCI_SUCCESS`.

- If the operation fails, the function returns `OCI_ERROR`.

**Related Topics**

- OCIContextClearValue()
