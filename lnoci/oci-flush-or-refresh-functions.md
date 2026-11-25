Lists and describes OCI flush or refresh functions.

Table 27-4 describes the OCI flush or refresh functions that are described in this section.

Table 27-4 Flush or Refresh Functions

| Function           | Purpose                                              |
|:-------------------|:-----------------------------------------------------|
| OCICacheFlush()    | Flush modified persistent objects in cache to server |
| OCICacheRefresh()  | Refresh pinned persistent objects                    |
| OCIObjectFlush()   | Flush a modified persistent object to the server     |
| OCIObjectRefresh() | Refresh a persistent object                          |

### 27.2.1 OCICacheFlush()

Flushes modified persistent objects to the server.

#### Purpose

Flushes modified persistent objects to the server.

#### Syntax

    sword OCICacheFlush ( OCIEnv              *env,
                          OCIError            *err,
                          const OCISvcCtx     *svc,
                          void                *context,
                          OCIRef              *(*get)
                                              ( void    *context,
                                                ub1     *last ),
                          OCIRef             **ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service context.

context (IN) \[optional\]
Specifies a user context that is an argument to the client callback function `get`. This parameter is set to `NULL` if there is no user context.

get (IN) \[optional\]
A client-defined function that acts as an iterator to retrieve a batch of dirty objects that need to be flushed. If the function is not `NULL`, this function is called to get a reference of a dirty object. This is repeated until a `NULL` reference is returned by the client function or the parameter `last` is set to `TRUE`. The parameter `context` is passed to `get()` for each invocation of the client function. This parameter should be `NULL` if user callback is not given. If the object that is returned by the client function is not a dirtied persistent object, the object is ignored.

All the objects that are returned from the client function must be newed or pinned using the same service context; otherwise, an error is signaled. Note that the cache flushes the returned objects in the order in which they were marked dirty.

If this parameter is passed as `NULL` (for example, no client-defined function is provided), then all dirty persistent objects for the given service context are flushed in the order in which they were dirtied.

ref (OUT) \[optional\]
If there is an error in flushing the objects, (`*ref`) points to the object that is causing the error. If `ref` is `NULL`, then the object is not returned. If `*ref` is `NULL`, then a reference is allocated and set to point to the object. If `*ref` is not `NULL`, then the reference of the object is copied into the given space. If the error is not caused by any of the dirtied objects, the given `REF` is initialized to be a `NULL` reference (`OCIRefIsNull(*ref`) is `TRUE`).

The `REF` is allocated for session duration (`OCI_DURATION_SESSION`). The application can free the allocated `REF` using the `OCIObjectFree()` function.

#### Comments

This function flushes the modified persistent objects from the object cache to the server. The objects are flushed in the order that they are new or marked as updated or marked as deleted.

**See Also:**

`OCIObjectFlush()`

This function incurs, at most, one network round-trip.

**Related Topics**

- OCIObjectFlush()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.2.2 OCICacheRefresh()

Refreshes all pinned persistent objects in the cache.

#### Purpose

Refreshes all pinned persistent objects in the cache.

#### Syntax

    sword OCICacheRefresh ( OCIEnv            *env,
                           OCIError           *err,
                           const OCISvcCtx    *svc,
                           OCIRefreshOpt       option,
                           void               *context,
                           OCIRef             *(*get)(void  *context),
                           OCIRef            **ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the description of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service context.

option (IN) \[optional\]
If `OCI_REFRESH_LOADED` is specified, all objects that are loaded within the transaction are refreshed. If the option is `OCI_REFRESH_LOADED` and the parameter `get` is not `NULL`, this function ignores the parameter.

context (IN) \[optional\]
Specifies a user context that is an argument to the client callback function `get`. This parameter is set to `NULL` if there is no user context.

get (IN) \[optional\]
A client-defined function that acts as an iterator to retrieve a batch of objects that need to be refreshed. If the function is not `NULL`, this function is called to get a reference of an object. If the reference is not `NULL`, then the object is refreshed. These steps are repeated until a `NULL` reference is returned by this function. The parameter `context` is passed to `get()` for each invocation of the client function. This parameter should be `NULL` if user callback is not given.

ref (OUT) \[optional\]
If there is an error in refreshing the objects, (`*ref`) points to the object that is causing the error. If `ref` is `NULL`, then the object is not returned. If `*ref` is `NULL`, then a reference is allocated and set to point to the object. If `*ref` is not `NULL`, then the reference of the object is copied into the given space. If the error is not caused by any of the objects, the given `ref` is initialized to be a `NULL` reference (`OCIRefIsNull(*ref`) is `TRUE`).

#### Comments

This function refreshes all pinned persistent objects and frees all unpinned persistent objects from the object cache.

**Note:**

When objects are refreshed, the secondary-level memory of those objects could potentially move to a different place in memory. As a result, any pointers to attributes that were saved prior to this call may be invalidated. Examples of attributes using secondary-level memory include `OCIString *`, `OCIColl *`, and `OCIRaw *`.

**Related Topics**

- OCIObjectRefresh()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Refreshing an Object Copy](object-advanced-topics-in-oci.md)

### 27.2.3 OCIObjectFlush()

Flushes a modified persistent object to the server.

#### Purpose

Flushes a modified persistent object to the server.

#### Syntax

    sword OCIObjectFlush ( OCIEnv        *env,
                           OCIError      *err,
                           void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to the persistent object. The object must be pinned before this call.

#### Comments

This function flushes a modified persistent object to the server. An exclusive lock is obtained implicitly for the object when it is flushed. When this function writes the object to the server, triggers may be fired. This function returns an error for transient objects and values, and for unmodified persistent objects.

Objects can be modified by triggers at the server. To keep objects in the cache consistent with the database, an application can free or refresh objects in the cache.

If the object to flush contains an internal LOB attribute and the LOB attribute was modified due to an `OCIObjectCopy()`, `OCILobAssign()`, or `OCILobLocatorAssign()` operation or by assigning another LOB locator to it, then the flush makes a copy of the LOB value that existed in the source LOB at the time of the assignment or copy of the internal LOB locator or object.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- OCICacheFlush()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectCopy()](oci-miscellaneous-object-functions.md)
- [OCILobAssign()](lob-functions.md)
- [OCILobLocatorAssign()](lob-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [LOB Functions](lob-functions.md)

### 27.2.4 OCIObjectRefresh()

Refreshes a persistent object from the most current database snapshot.

#### Purpose

Refreshes a persistent object from the most current database snapshot.

#### Syntax

    sword OCIObjectRefresh ( OCIEnv        *env,
                             OCIError      *err,
                             void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to the persistent object, which must already be pinned.

#### Comments

This function refreshes an object with data retrieved from the latest snapshot in the server. An object should be refreshed when the objects in the object cache are inconsistent with the objects in the server.

**Note:**

When an object is flushed to the server, triggers can be fired to modify more objects in the server. The same objects (modified by the triggers) in the object cache become out-of-date, and must be refreshed before they can be locked or flushed.

This occurs when the user issues a SQL statement or PL/SQL procedure to modify any object in the server.

**Note:**

Modifications made to objects (dirty objects) since the last flush are lost if unmarked objects are refreshed by this function.

Table 27-5 shows how the various meta-attribute flags and durations of an object are modified after being refreshed.

Table 27-5 Object Status After Refresh

| Object Attribute    | Status After Refresh     |
|:--------------------|:-------------------------|
| existent            | Set to appropriate value |
| pinned              | Unchanged                |
| allocation duration | Unchanged                |
| pin duration        | Unchanged                |

The object that is refreshed is replaced-in-place. When an object is replaced-in-place, the top-level memory of the object is reused so that new data can be loaded into the same memory address. The top-level memory of the `NULL` indicator structure is also reused. Unlike the top-level memory chunk, the secondary memory chunks are freed and reallocated.

You should be careful when writing functionality that retains a pointer to the secondary memory chunk, such as assigning the address of a secondary memory chunk to a local variable, because this pointer can become invalid after the object is refreshed.

This function does no affect transient objects or values.

**Related Topics**

- OCICacheRefresh()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
