Lists and describes cartridge services OCI external procedure functions.

Table 29-1 lists the OCI external procedure functions for C that are described in this section.

Table 29-1 External Procedures Functions

| Function                     | Purpose                                                     |
|:-----------------------------|:------------------------------------------------------------|
| OCIExtProcAllocCallMemory()  | Allocate memory for the duration of the External Procedure  |
| OCIExtProcGetEnv()           | Get the OCI environment, service context, and error handles |
| OCIExtProcRaiseExcp()        | Raise an Exception to PL/SQL                                |
| OCIExtProcRaiseExcpWithMsg() | Raise an exception with a message                           |

### 29.2.1 OCIExtProcAllocCallMemory()

Allocates N bytes of memory for the duration of the external procedure.

#### Purpose

Allocates N bytes of memory for the duration of the external procedure.

#### Syntax

    void  * OCIExtProcAllocCallMemory ( OCIExtProcContext    *with_context,
                                        size_t                amount );

#### Parameters

with_context (IN)
The `with_context` pointer that is passed to the C external procedure.

`With_Context` Type — The C callable interface to PL/SQL external procedures requires the `with_context` parameter to be passed. The type of this structure is `OCIExtProcContext`, which is opaque to the user.

The user can declare the `with_context` parameter in the application as follows:

    OCIExtProcContext *with_context;

<!-- -->

amount (IN)
The number of bytes to allocate.

#### Comments

This call allocates `amount` bytes of memory for the duration of the call of the external procedure.

Any memory allocated by this call is freed by PL/SQL upon return from the external procedure. The application must not use any kind of `free()` function on memory allocated by `OCIExtProcAllocCallMemory()`. Use this function to allocate memory for function returns.

A zero return value should be treated as an error.

#### Returns

An untyped (opaque) pointer to the allocated memory.

#### Example

Using OCIExtProcAllocCallMemory() to Allocate 1024 Bytes of Memory

    text *ptr = (text *)OCIExtProcAllocCallMemory(wctx, 1024)

**Related Topics**

- [OCIMemoryAlloc()](cartridge-services-memory-services.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 29.2.2 OCIExtProcGetEnv()

Gets the OCI environment, service context, and error handles.

#### Purpose

Gets the OCI environment, service context, and error handles.

#### Syntax

    sword OCIExtProcGetEnv ( OCIExtProcContext     *with_context,
                             OCIEnv               **envh,
                             OCISvcCtx            **svch,
                             OCIError             **errh );

#### Parameters

with_context (IN)
The `with_context` pointer that is passed to the C external procedure.

`With_Context` Type — The C callable interface to PL/SQL external procedures requires the `with_context` parameter to be passed. The type of this structure is `OCIExtProcContext`, which is opaque to the user.

The user can declare the `with_context` parameter in the application as follows:

    OCIExtProcContext *with_context;

envh (OUT)
Pointer to a variable to store the OCI environment handle.

svch (OUT)
Pointer to a variable to store the OCI service handle.

errh (OUT)
Pointer to a variable to store the OCI error handle.

#### Comments

The primary purpose of this function is to allow OCI callbacks to use the database in the same transaction. The OCI handles obtained by this function should be used in OCI callbacks to the database. If these handles are obtained through standard OCI calls, then these handles use a new connection to the database and cannot be used for callbacks in the same transaction. In one external procedure you can use either callbacks or a new connection, but not both.

Example of a call:

    OCIEnv    *envh;
    OCISvcCtx *svch;
    OCIError  *errh;
    ...
    OCIExtProcGetEnv(ctx,&envh,&svch,&errh);

#### Returns

This function returns `OCI_SUCCESS` if the call succeeds; otherwise, it returns `OCI_ERROR`.

**Related Topics**

- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIArrayDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCIHandleAlloc()](handle-and-descriptor-functions.md)

### 29.2.3 OCIExtProcRaiseExcp()

Raises an Exception to PL/SQL.

#### Purpose

Raises an Exception to PL/SQL.

#### Syntax

    size_t OCIExtProcRaiseExcp ( OCIExtProcContext    *with_context,
                                 int                   errnum );

#### Parameters

with_context (IN)
The `with_context` pointer that is passed to the C external procedure.

`With_Context` Type — The C callable interface to PL/SQL external procedures requires the `with_context` parameter to be passed. The type of this structure is `OCIExtProcContext`, which is opaque to the user.

The user can declare the `with_context` parameter in the application as follows:

    OCIExtProcContext *with_context;

<!-- -->

errnum (IN)
Oracle Database error number to signal to PL/SQL. The `errnum` value must be a positive number and in the range 1 to 32767.

#### Comments

Calling this function signals an exception to PL/SQL. After a successful return from this function, the external procedure must start its exit handling and return to PL/SQL. Once an exception is signaled to PL/SQL, IN/OUT and OUT arguments, if any, are not processed at all.

#### Returns

This function returns `OCIEXTPROC_SUCCESS` if the call succeeds. It returns `OCIEXTPROC_ERROR` if the call fails.

**Related Topics**

- OCIExtProcRaiseExcpWithMsg()

### 29.2.4 OCIExtProcRaiseExcpWithMsg()

Raises an exception with a message.

#### Purpose

Raises an exception with a message.

#### Syntax

    size_t OCIExtProcRaiseExcpWithMsg ( OCIExtProcContext    *with_context,
                                        int                   errnum,
                                        char                 *errmsg,
                                        size_t                msglen );

#### Parameters

with_context (IN)
The `with_context` pointer that is passed to the C external procedure.

`With_Context` Type — The C callable interface to PL/SQL external procedures requires the `with_context` parameter to be passed. The type of this structure is `OCIExtProcContext`, which is opaque to the user.

The user can declare the `with_context` parameter in the application as follows:

    OCIExtProcContext *with_context;

<!-- -->

errnum (IN)
Oracle Database error number to signal to PL/SQL. The value of `errnum` must be a positive number and in the range 1 to 32767

errmsg (IN)
The error message associated with `errnum`.

msglen (IN)
The length of the error message. Pass zero if `errmsg` is a `NULL`-terminated string.

#### Comments

This call raises an exception to PL/SQL. In addition, it substitutes the following error message string within the standard Oracle Database error message string.

#### Returns

This function returns `OCIEXTPROC_SUCCESS` if the call succeeds. It returns `OCIEXTPROC_ERROR` if the call fails.

**Related Topics**

- OCIExtProcRaiseExcp()
