Lists and describes cartridge services memory services functions.

Table 29-2 lists the memory services functions that are described in this section.

Table 29-2 Memory Services Functions

| Function           | Purpose                                               |
|:-------------------|:------------------------------------------------------|
| OCIDurationBegin() | Start a user duration                                 |
| OCIDurationEnd()   | Terminate a user duration                             |
| OCIMemoryAlloc()   | Allocate memory of a given size from a given duration |
| OCIMemoryFree()    | Free a memory chunk                                   |
| OCIMemoryResize()  | Resize a memory chunk                                 |

**See Also:**

[Oracle Database Data Cartridge Developer's Guide](../addci/using-cartridge-services.md) for more information about using these functions

### 29.3.1 OCIDurationBegin()

Starts a user duration.

#### Purpose

Starts a user duration.

#### Syntax

    sword OCIDurationBegin ( OCIEnv              *env,
                             OCIError            *err,
                             const OCISvcCtx     *svc,
                             OCIDuration          parent,
                             OCIDuration         *duration );

#### Parameters

env (IN/OUT)
The OCI environment handle. This should be passed as `NULL` for cartridge services.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

svc (IN)
The OCI service context handle.

parent (IN)
The duration number of the parent duration. It is one of the following:

- A user duration that was previously created

- `OCI_DURATION_STATEMENT`

- `OCI_DURATION_SESSION`

duration (OUT)
An identifier unique to the newly created user duration.

#### Comments

This function starts a user duration. A user can have multiple active user durations simultaneously. The user durations do not have to be nested. The `duration` parameter is used to return a number that uniquely identifies the duration created by this call.

Note that the environment and service context parameters cannot both be `NULL`.

**Related Topics**

- [OCIDurationEnd()](lob-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.3.2 OCIDurationEnd()

Terminates a user duration.

#### Purpose

Terminates a user duration.

#### Syntax

    sword OCIDurationEnd ( OCIEnv             *env,
                           OCIError           *err,
                           const OCISvcCtx    *svc,
                           OCIDuration         duration );

#### Parameters

env (IN/OUT)
The OCI environment handle.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

svc (IN)
OCI service context (this should be passed as `NULL` for cartridge services; otherwise, it should be non-`NULL`).

duration (IN)
A user duration previously created by `OCIDurationBegin()`.

#### Comments

This function terminates a user duration.

Note that the environment and service context parameters cannot both be `NULL`.

### 29.3.3 OCIMemoryAlloc()

Allocates memory of a given size from a given duration.

#### Purpose

Allocates memory of a given size from a given duration.

#### Syntax

    sword OCIMemoryAlloc( void         *hndl,
                          OCIError     *err,
                          void        **mem,
                          OCIDuration   dur,
                          ub4           size,
                          ub4           flags );

#### Parameters

hndl (IN)
The OCI environment handle (`OCIEnv *`) if `dur` is `OCI_DURATION_PROCESS`; otherwise, the user session handle (`OCISession *`).

err (IN)
The error handle.

mem (OUT)
Memory allocated.

dur (IN)
A previously created user duration or one of these values:

`OCI_DURATION_CALLOUT`

`OCI_DURATION_STATEMENT`

`OCI_DURATION_SESSION`

`OCI_DURATION_PROCESS`

size (IN)
Size of memory to be allocated.

flags (IN)
Set the `OCI_MEMORY_CLEARED` bit to get memory that has been cleared.

#### Comments

To allocate memory for the duration of the callout of the agent, that is, external procedure duration, use `OCIExtProcAllocCallMemory()` or `OCIMemoryAlloc()` with `dur` as `OCI_DURATION_CALLOUT`.

#### Returns

Error code.

**Related Topics**

- [OCIExtProcAllocCallMemory()](cartridge-services-oci-external-procedures.md)

### 29.3.4 OCIMemoryFree()

Frees a memory chunk.

#### Purpose

Frees a memory chunk.

#### Syntax

    sword OCIMemoryFree ( void     *hndl,
                          OCIError *err,
                          void     *mem );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

mem (IN/OUT)
Pointer to memory allocated previously using `OCIMemoryAlloc()`.

#### Returns

Error code.

**Related Topics**

- OCIMemoryAlloc()

### 29.3.5 OCIMemoryResize()

Resizes a memory chunk to a new size.

#### Purpose

Resizes a memory chunk to a new size.

#### Syntax

    sword OCIMemoryResize( void          *hndl,
                           OCIError      *err,
                           void         **mem,
                           ub4            newsize,
                           ub4            flags );

#### Parameters

hndl (IN)
The OCI environment or user session handle.

err (IN)
The error handle.

mem (IN/OUT)
Pointer to memory allocated previously using `OCIMemoryAlloc()`.

newsize (IN)
Size of memory requested.

flags (IN)
Set the `OCI_MEMORY_CLEARED` bit to get memory that has been cleared.

#### Comments

Memory must have been allocated before this function can be called to resize.

#### Returns

Error code.

**Related Topics**

- OCIMemoryAlloc()
