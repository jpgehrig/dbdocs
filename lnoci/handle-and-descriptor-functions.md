Lists and describes the OCI handle and descriptor functions.

Table 25-3 lists the OCI handle and descriptor functions that are described in this section.

Table 25-3 Handle and Descriptor Functions  

| Function                  | Purpose                                                 |
|:--------------------------|:--------------------------------------------------------|
| OCIArrayDescriptorAlloc() | Allocate an array of descriptors                        |
| OCIArrayDescriptorFree()  | Free an array of descriptors                            |
| OCIAttrGet()              | Get the value of an attribute of a handle               |
| OCIAttrSet()              | Set the value of an attribute of a handle or descriptor |
| OCIDescriptorAlloc()      | Allocate and initialize a descriptor or LOB locator     |
| OCIDescriptorFree()       | Free a previously allocated descriptor                  |
| OCIHandleAlloc()          | Allocate and initialize a handle                        |
| OCIHandleFree()           | Free a previously allocated handle                      |
| OCIParamGet()             | Get a parameter descriptor                              |
| OCIParamSet()             | Set parameter descriptor in COR handle                  |

### 25.3.1 OCIArrayDescriptorAlloc()

Allocates an array of descriptors.

#### Purpose

Allocates an array of descriptors.

#### Syntax

    sword OCIArrayDescriptorAlloc ( const void    *parenth,
                                    void         **descpp,
                                    const ub4      type,
                                    ub4            array_size,
                                    const size_t   xtramem_sz,
                                    void         **usrmempp);

#### Parameters

parenth (IN)
An environment handle.

descpp (OUT)
Returns a pointer to a contiguous array of descriptors of the desired type.

type (IN)
Specifies the type of descriptor or LOB locator to be allocated. For a list of types, see `OCIDescriptorAlloc()`.

array_size (IN)
Specifies the number of descriptors to allocate. An error is thrown when the call cannot allocate the number of descriptors.

<!-- -->

xtramem_sz (IN)
Specifies an amount of user memory to be allocated for use by the application for the lifetime of the descriptors.

usrmempp (OUT)
Returns a pointer to an array of pointers numbering in `array_size`, since there is one chunk allocated for each of the descriptors allocated.

#### Comments

This call returns `OCI_SUCCESS` if successful, or a suitable error if an out-of-memory condition occurs.

**See Also:**

[User Memory Allocation](oci-programming-basics.md) for more information about the `xtramem_sz` parameter and user memory allocation

#### Example

The following code example can be modified to allocate a large number of descriptors.

Allocating a Large Number of Descriptors

    OCIDateTime *descpp1[500];
    ...
    for (i = 0; i!=500; i++)
    {
         /* Allocate descriptors */
    OCIDescriptorAlloc((void  *)envhp,(void  **)&descpp1[i], OCI_DTYPE_TIMESTAMP_TZ,
                       0,(void  **)0);
    }
    ...

The for loop in the previous code example can now be replaced with a single call, as shown in the following code example.

Allocating an Array of Descriptors

    OCIArrayDescriptorAlloc((void *)envhp,(void **)&descpp1,
                            OCI_DTYPE_TIMESTAMP_TZ, 500, 0, (void **)0);

**Related Topics**

- OCIDescriptorAlloc()
- OCIArrayDescriptorFree()

### 25.3.2 OCIArrayDescriptorFree()

Free a previously allocated array of descriptors.

#### Purpose

Free a previously allocated array of descriptors.

#### Syntax

    sword OCIArrayDescriptorFree ( void       **descp,
                                   const ub4    type );

#### Parameters

descp (IN)
Pointer to an array of allocated descriptors.

type (IN)
Specifies the type of storage to be freed. See the types listed in `OCIDescriptorAlloc()`.

#### Comments

An error is returned when a descriptor is allocated using `OCIDescriptorAlloc()`, but freed using `OCIArrayDescriptorFree()`.

If you perform LOB operations, you must always call `OCILobFreeTemporary()` before calling `OCIArrayDescriptorFree()` to free the contents of the temporary LOB. See [About Freeing Temporary LOBs](lobs-and-bfile-operations.md) for more information.

Descriptors allocated using `OCIArrayDescriptorAlloc()` must be freed using `OCIArrayDescriptorFree()`. You must be careful to free the entire array at once: pass in the pointer `descpp` returned by `OCIArrayDescriptorAlloc()` to `OCIArrayDescriptorFree()` appropriately. Otherwise, there can be memory leaks.

**Related Topics**

- OCIArrayDescriptorAlloc()
- OCIDescriptorAlloc()

### 25.3.3 OCIAttrGet()

Gets the value of an attribute of a handle.

#### Purpose

Gets the value of an attribute of a handle.

#### Syntax

    sword OCIAttrGet ( const void     *trgthndlp,
                       ub4             trghndltyp,
                       void           *attributep,
                       ub4            *sizep,
                       ub4             attrtype,
                       OCIError       *errhp );

#### Parameters

trgthndlp (IN)
Pointer to a handle type. The actual handle can be a statement handle, a session handle, and so on. When this call is used to get encoding, users are allowed to check against either an environment or statement handle.

trghndltyp (IN)
The handle type. Valid types are:

- `OCI_DTYPE_PARAM`, for a parameter descriptor

- `OCI_HTYPE_STMT`, for a statement handle

- Any handle type in [Table 4-1](oci-programming-basics.md) or any descriptor in [Table 4-2](oci-programming-basics.md).

attributep (OUT)
Pointer to the storage for an attribute value. Is in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

sizep (OUT)
The size of the attribute value, always in bytes because `attributep` is a `void` pointer. This can be passed as `NULL` for most attributes because the sizes of non-string attributes are already known by the OCI library. For `text*` parameters, a pointer to a `ub4` must be passed in to get the length of the string.

attrtype (IN)
The type of attribute being retrieved. The handle types and their readable attributes are listed in [Handle and Descriptor Attributes](handle-and-descriptor-attributes.md).

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

This call is used to get a particular attribute of a handle. `OCI_DTYPE_PARAM` is used to do implicit and explicit describes. The parameter descriptor is also used in direct path loading. For implicit describes, the parameter descriptor has the column description for each select list. For explicit describes, the parameter descriptor has the describe information for each schema object that you are trying to describe. If the top-level parameter descriptor has an attribute that is itself a descriptor, use `OCI_ATTR_PARAM` as the attribute type in the subsequent call to `OCIAttrGet()` to get the Unicode information in an environment or statement handle.

**See Also:**

[Examples Using OCIDescribeAny()](describing-schema-metadata.md) and [About Describing Select-List Items](using-sql_statements-in-oci.md)

A function closely related to `OCIAttrGet()` is `OCIDescribeAny()`, which is a generic describe call that describes existing schema objects: tables, views, synonyms, procedures, functions, packages, sequences, and types. As a result of this call, the describe handle is populated with the object-specific attributes that can be obtained through an `OCIAttrGet()` call.

Then an `OCIParamGet()` call on the describe handle returns a parameter descriptor for a specified position. Parameter positions begin with 1. Calling `OCIAttrGet()` on the parameter descriptor returns the specific attributes of a stored procedure or function parameter or a table column descriptor. These subsequent calls do not need an extra round-trip to the server because the entire schema object description is cached on the client side by `OCIDescribeAny()`. Calling `OCIAttrGet()` on the describe handle can also return the total number of positions.

In `UTF-16` mode, particularly when executing a loop, try to reuse the same pointer variable corresponding to an attribute and copy the contents to local variables after `OCIAttrGet()` is called. If multiple pointers are used for the same attribute, a memory leak can occur.

**Related Topics**

- OCIAttrSet()
- [OCIDescribeAny()](bind-define-describe-functions.md)
- OCIParamGet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.3.4 OCIAttrSet()

Sets the value of an attribute of a handle or a descriptor.

#### Purpose

Sets the value of an attribute of a handle or a descriptor.

#### Syntax

    sword OCIAttrSet ( void        *trgthndlp,
                       ub4          trghndltyp,
                       void        *attributep,
                       ub4          size,
                       ub4          attrtype,
                       OCIError    *errhp );

#### Parameters

trgthndlp (IN/OUT)
Pointer to a handle whose attribute gets modified.

trghndltyp (IN/OUT)
The handle type.

attributep (IN)
Pointer to an attribute value. The attribute value is copied into the target handle. If the attribute value is a pointer, then only the pointer is copied, not the contents of the pointer. String attributes must be in the encoding specified by the `charset` parameter of a previous call to `OCIEnvNlsCreate()`.

size (IN)
The size of an attribute value. This can be passed in as 0 for most attributes, as the size is already known by the OCI library. For `text*` attributes, a `ub4` must be passed in set to the length of the string in bytes, regardless of encoding.

attrtype (IN)
The type of attribute being set.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

#### Comments

See [Handle and Descriptor Attributes](handle-and-descriptor-attributes.md) for a list of handle types and their writable attributes.

**Related Topics**

- OCIArrayDescriptorAlloc()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 25.3.5 OCIDescriptorAlloc()

Allocates storage to hold descriptors or LOB locators.

#### Purpose

Allocates storage to hold descriptors or LOB locators.

#### Syntax

    sword OCIDescriptorAlloc ( const void    *parenth,
                               void         **descpp,
                               ub4            type,
                               size_t         xtramem_sz,
                               void         **usrmempp);

#### Parameters

parenth (IN)
An environment handle.

descpp (OUT)
Returns a descriptor or LOB locator of the desired type.

type (IN)
Specifies the type of descriptor or LOB locator to be allocated:

- `OCI_DTYPE_SNAP` - Specifies generation of snapshot descriptor of C type `OCISnapshot`.

- `OCI_DTYPE_LOB` - Specifies generation of a LOB value type locator (for a `BLOB` or `CLOB`) of C type `OCILobLocator`.

- `OCI_DTYPE_FILE` - Specifies generation of a FILE value type locator of C type `OCILobLocator`.

- `OCI_DTYPE_ROWID` - Specifies generation of a `ROWID` descriptor of C type `OCIRowid`.

- `OCI_DTYPE_DATE` - Specifies generation of an `ANSI` `DATE` descriptor of C type `OCIDateTime`.

- `OCI_DTYPE_PARAM` - Specifies generation of a read-only parameter descriptor of C type `OCIParam`.

- `OCI_DTYPE_TIMESTAMP` - Specifies generation of a `TIMESTAMP` descriptor of C type `OCIDateTime`.

- `OCI_DTYPE_TIMESTAMP_TZ` - Specifies generation of a `TIMESTAMP` `WITH` `TIME` `ZONE` descriptor of C type `OCIDateTime`.

- `OCI_DTYPE_TIMESTAMP_LTZ` - Specifies generation of a `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` descriptor of C type `OCIDateTime`.

- `OCI_DTYPE_INTERVAL_YM` - Specifies generation of an `INTERVAL` `YEAR` `TO` `MONTH` descriptor of C type `OCIInterval`.

- `OCI_DTYPE_INTERVAL_DS` - Specifies generation of an `INTERVAL` `DAY` `TO` `SECOND` descriptor of C type `OCIInterval`.

- `OCI_DTYPE_COMPLEXOBJECTCOMP` - Specifies generation of a complex object retrieval descriptor of C type `OCIComplexObjectComp`.

- `OCI_DTYPE_AQENQ_OPTIONS` - Specifies generation of an Advanced Queuing enqueue options descriptor of C type `OCIAQEnqOptions`.

- `OCI_DTYPE_AQDEQ_OPTIONS` - Specifies generation of an Advanced Queuing dequeue options descriptor of C type `OCIAQDeqOptions`.

- `OCI_DTYPE_AQMSG_PROPERTIES` - Specifies generation of an Advanced Queuing message properties descriptor of C type `OCIAQMsgProperties`.

- `OCI_DTYPE_AQAGENT` - Specifies generation of an Advanced Queuing agent descriptor of C type `OCIAQAgent`.

- `OCI_DTYPE_AQNFY` - Specifies generation of an Advanced Queuing notification descriptor of C type `OCIAQNotify`.

- `OCI_DTYPE_AQLIS_OPTIONS` - Specifies generation of an Advanced Queuing listen descriptor of C type `OCIAQListenOpts`.

- `OCI_DTYPE_AQLIS_MSG_PROPERTIES` - Specifies generation of an Advanced Queuing message properties descriptor of C type `OCIAQLisMsgProps`.

- `OCI_DTYPE_SHARDING_KEY` - Specifies generation of the shard key or the shard group key of C type `OCIShardingKey`.

- `OCI_DTYPE_SRVDN` - Specifies generation of a Distinguished Names descriptor of C type `OCIServerDNs`.

- `OCI_DTYPE_UCB` - Specifies generation of a user callback descriptor of C type `OCIUcb`.

xtramem_sz (IN)
Specifies an amount of user memory to be allocated for use by the application for the lifetime of the descriptor.

usrmempp (OUT)
Returns a pointer to the user memory of size `xtramem_sz` allocated by the call for the user for the lifetime of the descriptor.

#### Comments

Returns a pointer to an allocated and initialized descriptor, corresponding to the type specified in `type`. A non-`NULL` descriptor or LOB locator is returned on success. No diagnostics are available on error.

This call returns `OCI_SUCCESS` if successful, or `OCI_INVALID_HANDLE` if an out-of-memory error occurs.

**Related Topics**

- OCIDescriptorFree()
- OCIArrayDescriptorAlloc()
- OCIArrayDescriptorFree()

**See Also:**

[User Memory Allocation](oci-programming-basics.md) for more information about the `xtramem_sz` parameter and user memory allocation

### 25.3.6 OCIDescriptorFree()

Deallocates a previously allocated descriptor.

#### Purpose

Deallocates a previously allocated descriptor.

#### Syntax

    sword OCIDescriptorFree ( void     *descp,
                              ub4       type );

#### Parameters

descp (IN)
An allocated descriptor.

type (IN)
Specifies the type of storage to be freed. See the types listed in `OCIDescriptorAlloc()`.

#### Comments

This call frees storage associated with a descriptor. Returns `OCI_SUCCESS` or `OCI_INVALID_HANDLE`. All descriptors can be explicitly deallocated; however, OCI deallocates a descriptor if the environment handle is deallocated.

If you perform LOB operations, you must always call `OCILobFreeTemporary()` before calling `OCIDescriptorFree()` to free the contents of the temporary LOB. See [About Freeing Temporary LOBs](lobs-and-bfile-operations.md) for more information.

**Related Topics**

- OCIDescriptorAlloc()

### 25.3.7 OCIHandleAlloc()

Returns a pointer to an allocated and initialized handle.

#### Purpose

Returns a pointer to an allocated and initialized handle.

#### Syntax

    sword OCIHandleAlloc ( const void    *parenth,
                           void         **hndlpp,
                           ub4            type,
                           size_t         xtramem_sz,
                           void         **usrmempp );

#### Parameters

parenth (IN)
An environment handle.

hndlpp (OUT)
Returns a handle.

type (IN)
Specifies the type of handle to be allocated. The allowed handles are described in [Table 4-1](oci-programming-basics.md).

<!-- -->

xtramem_sz (IN)
Specifies an amount of user memory to be allocated.

usrmempp (OUT)
Returns a pointer to the user memory of size `xtramem_sz` allocated by the call for the user.

#### Comments

Returns a pointer to an allocated and initialized handle, corresponding to the type specified in `type`. A non-`NULL` handle is returned on success. All handles are allocated with respect to an environment handle that is passed in as a parent handle.

No diagnostics are available on error. This call returns `OCI_SUCCESS` if successful, or `OCI_INVALID_HANDLE` if an error occurs.

Handles must be allocated using `OCIHandleAlloc()` before they can be passed into an OCI call.

**Related Topics**

- OCIHandleFree()

**See Also:**

[User Memory Allocation](oci-programming-basics.md) for more information about using the `xtramem_sz` parameter for user memory allocation

### 25.3.8 OCIHandleFree()

Explicitly deallocates a handle

#### Purpose

This call explicitly deallocates a handle.

#### Syntax

    sword OCIHandleFree ( void      *hndlp,
                          ub4        type );

#### Parameters

hndlp (IN)
A handle allocated by `OCIHandleAlloc()`.

type (IN)
Specifies the type of storage to be freed. The handles are described in [Table 4-1](oci-programming-basics.md).

#### Comments

This call frees up storage associated with a handle, corresponding to the type specified in the `type` parameter.

This call returns either `OCI_SUCCESS`, `OCI_INVALID_HANDLE`, or `OCI_ERROR`.

All handles may be explicitly deallocated. The OCI deallocates a child handle if the parent is deallocated.

When a statement handle is freed, the cursor associated with the statement handle is closed, but the actual cursor closing may be deferred to the next round-trip to the server. If the application must close the cursor immediately, you can make a server round-trip call, such as `OCIServerVersion()` or `OCIPing()`, after the `OCIHandleFree()` call.

**Related Topics**

- OCIHandleAlloc()
- [OCIServerVersion()](miscellaneous-functions.md)
- [OCIPing()](miscellaneous-functions.md)

### 25.3.9 OCIParamGet()

Returns a descriptor of a parameter specified by position in the describe handle or statement handle.

#### Purpose

Returns a descriptor of a parameter specified by position in the describe handle or statement handle.

#### Syntax

    sword OCIParamGet ( const void        *hndlp,
                        ub4                htype,
                        OCIError          *errhp,
                        void             **parmdpp,
                        ub4                pos );

#### Parameters

hndlp (IN)
A statement handle or describe handle. The `OCIParamGet()` function returns a parameter descriptor for this handle.

htype (IN)
The type of the handle passed in the `hndlp` parameter. Valid types are:

- `OCI_DTYPE_PARAM`, for a parameter descriptor

- `OCI_HTYPE_COMPLEXOBJECT`, for a complex object retrieval handle

- `OCI_HTYPE_STMT`, for a statement handle

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

parmdpp (OUT)
A descriptor of the parameter at the position given in the `pos` parameter, of handle type `OCI_DTYPE_PARAM`.

pos (IN)
Position number in the statement handle or describe handle. A parameter descriptor is returned for this position.

**Note:**

`OCI_ERROR` is returned if there are no parameter descriptors for this position.

#### Comments

This call returns a descriptor of a parameter specified by position in the describe handle or statement handle. Parameter descriptors are always allocated internally by the OCI library. They can be freed using `OCIDescriptorFree()`. For example, if you fetch the same column metadata for every execution of a statement, then the program leaks memory unless you explicitly free the parameter descriptor between each call to `OCIParamGet()`.

**Related Topics**

- OCIArrayDescriptorAlloc()
- OCIAttrSet()
- OCIParamSet()
- OCIDescriptorFree()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Handle and Descriptor Attributes](handle-and-descriptor-attributes.md) for more detailed information about parameter descriptor attributes

### 25.3.10 OCIParamSet()

Sets a complex object retrieval (COR) descriptor into a COR handle.

#### Purpose

Sets a complex object retrieval (COR) descriptor into a COR handle.

#### Syntax

    sword OCIParamSet ( void           *hndlp,
                        ub4             htype,
                        OCIError       *errhp,
                        const void     *dscp,
                        ub4             dtyp,
                        ub4             pos );

#### Parameters

hndlp (IN/OUT)
Handle pointer.

htype (IN)
Handle type.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information when there is an error.

dscp (IN)
Complex object retrieval descriptor pointer.

dtyp (IN)
Descriptor type. The descriptor type for a COR descriptor is `OCI_DTYPE_COMPLEXOBJECTCOMP`.

pos (IN)
Position number.

#### Comments

The COR handle must have been previously allocated using `OCIHandleAlloc()`, and the descriptor must have been previously allocated using `OCIDescriptorAlloc()`. Attributes of the descriptor are set using `OCIAttrSet()`.

**Related Topics**

- OCIParamGet()
- OCIHandleAlloc()
- OCIDescriptorAlloc()
- OCIAttrSet()
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

[Complex Object Retrieval](oci-object-relational-programming.md) for more information about complex object retrieval
