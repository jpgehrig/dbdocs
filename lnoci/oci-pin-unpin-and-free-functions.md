Lists and describes the OCI pin, unpin, and free functions.

Table 27-10 describes the OCI pin, unpin, and free functions that are described in this section.

Table 27-10 Pin, Unpin, and Free Functions

| Function                 | Purpose                                         |
|:-------------------------|:------------------------------------------------|
| OCICacheFree()           | Free objects in the cache                       |
| OCICacheUnpin()          | Unpin persistent objects in cache or connection |
| OCIObjectArrayPin()      | Pin an array of references                      |
| OCIObjectFree()          | Free a previously allocated object              |
| OCIObjectPin()           | Pin an object                                   |
| OCIObjectPinCountReset() | Unpin an object to zero pin count               |
| OCIObjectPinTable()      | Pin a table object with a given duration        |
| OCIObjectUnpin()         | Unpin an object                                 |

### 27.6.1 OCICacheFree()

Frees all objects and values in the cache for the specified connection.

#### Purpose

Frees all objects and values in the cache for the specified connection.

#### Syntax

    sword OCICacheFree ( OCIEnv              *env,
                         OCIError            *err,
                         const OCISvcCtx     *svc );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
An OCI service context.

#### Comments

If a connection is specified, this function frees the persistent objects, transient objects and values allocated for that connection. Otherwise, all persistent objects, transient objects and values in the object cache are freed. Objects are freed regardless of their pin count.

**Related Topics**

- OCIObjectFree()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

`OCIObjectFree()` for more information about freeing an instance

### 27.6.2 OCICacheUnpin()

Unpins persistent objects.

#### Purpose

Unpins persistent objects.

#### Syntax

    sword OCICacheUnpin ( OCIEnv              *env,
                          OCIError            *err,
                          const OCISvcCtx     *svc );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
An OCI service context handle. The objects on the specified connection are unpinned.

#### Comments

This function completely unpins all of the persistent objects for the given connection. The pin count for the objects is reset to zero.

**Related Topics**

- OCIObjectUnpin()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [Pinning an Object](oci-object-relational-programming.md)
- [Pin Count and Unpinning](oci-object-relational-programming.md)

### 27.6.3 OCIObjectArrayPin()

Pins an array of references.

#### Purpose

Pins an array of references.

#### Syntax

    sword OCIObjectArrayPin ( OCIEnv            *env,
                              OCIError          *err,
                              OCIRef           **ref_array,
                              ub4                array_size,
                              OCIComplexObject **cor_array,
                              ub4                cor_array_size,
                              OCIPinOpt          pin_option,
                              OCIDuration        pin_duration,
                              OCILockOpt         lock,
                              void             **obj_array,
                              ub4               *pos );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ref_array (IN)
Array of references to be pinned.

array_size (IN)
Number of elements in the array of references.

cor_array
An array of COR handles corresponding to the objects being pinned.

cor_array_size
The number of elements in `cor_array`.

pin_option (IN)
Pin option.

**See Also:**

`OCIObjectPin()`

<!-- -->

pin_duration (IN)
Pin duration. See `OCIObjectPin()`.

lock (IN)
Lock option. See `OCIObjectPin()`.

obj_array (OUT)
If this argument is not `NULL`, the pinned objects are returned in the array. The user must allocate this array with the element type being `void *`. The size of this array is identical to `array_size`.

pos (OUT)
If there is an error, this argument indicates the element that is causing the error. Note that this argument is set to 1 for the first element in the `ref_array`.

#### Comments

All the pinned objects are retrieved from the database in one network round-trip. If the user specifies an output array (`obj_array`), then the address of the pinned objects are assigned to the elements in the array.

**Related Topics**

- OCIObjectPin()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.6.4 OCIObjectFree()

Frees and unpins an object instance.

#### Purpose

Frees and unpins an object instance.

#### Syntax

    sword OCIObjectFree ( OCIEnv          *env,
                          OCIError        *err,
                          void            *instance,
                          ub2              flags );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
Pointer to a standalone instance. If it is an object, it must be pinned.

flags (IN)
If `OCI_OBJECTFREE_FORCE` is passed, free the object even if it is pinned or dirty. If `OCI_OBJECTFREE_NONULL` is passed, the `NULL` structure is not freed.

#### Comments

This function deallocates all the memory allocated for an object instance, including the `NULL` structure. The following rules apply to different instance types:

For Persistent Objects
This function returns an error if the client is attempting to free a dirty persistent object that has not been flushed. The client should either flush the persistent object, unmark it, or set the parameter `flags` to `OCI_OBJECTFREE_FORCE`.

This function calls `OCIObjectUnpin()` once to check if the object can be completely unpinned. If it succeeds, the rest of the function proceeds to free the object. If it fails, then an error is returned unless the parameter `flags` is set to `OCI_OBJECTFREE_FORCE`.

Freeing a persistent object in memory does not change the persistent state of that object at the server. For example, the object remains locked after the object is freed.

For Transient Objects
This function calls `OCIObjectUnpin()` once to check if the object can be completely unpinned. If it succeeds, the rest of the function proceeds to free the object. If it fails, then an error is returned unless the parameter `flags` is set to `OCI_OBJECTFREE_FORCE`.

For Values
The memory of the object is freed immediately.

**Related Topics**

- OCICacheFree()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.6.5 OCIObjectPin()

Pins a referenceable object.

#### Purpose

Pins a referenceable object.

#### Syntax

    sword OCIObjectPin ( OCIEnv              *env,
                         OCIError            *err,
                         OCIRef              *object_ref,
                         OCIComplexObject    *corhdl,
                         OCIPinOpt            pin_option,
                         OCIDuration          pin_duration,
                         OCILockOpt           lock_option,
                         void               **object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object_ref (IN)
The reference to the object.

corhdl (IN)
Handle for complex object retrieval.

pin_option (IN)
Used to specify the copy of the object that is to be retrieved.

pin_duration (IN)
The duration during which the object is being accessed by a client. The object is implicitly unpinned at the end of the pin duration. If `OCI_DURATION_NULL` is passed, there is no pin promotion if the object is already loaded into the cache. If the object is not yet loaded, then the pin duration is set to `OCI_DURATION_DEFAULT` for `OCI_DURATION_NULL`.

lock_option (IN)
Lock option (for example, exclusive). If a lock option is specified, the object is locked in the server. The lock status of an object can also be retrieved by calling `OCIObjectIsLocked()`. Valid values include:

- `OCI_LOCK_NONE` (no lock)

- `OCI_LOCK_X` (exclusive lock)

- `OCI_LOCK_X_NOWAIT` (exclusive lock with the `NOWAIT` option)

  **See Also:**

  [About Locking with the NOWAIT Option](object-advanced-topics-in-oci.md)

object (OUT)
The pointer to the pinned object.

#### Comments

This function pins a referenceable object instance when given the object reference. The process of pinning serves two purposes:

- It locates an object given its reference. This is done by the object cache that keeps track of the objects in the object cache.

- It notifies the object cache that a persistent object is being used such that the persistent object cannot be aged out. Because a persistent object can be loaded from the server whenever is needed, the memory utilization can be increased if a completely unpinned persistent object can be freed (aged out) even before the allocation duration is expired. An object can be pinned many times. A pinned object remains in memory until it is completely unpinned.

  **See Also:**

  `OCIObjectUnpin()`

For Persistent Objects
When pinning a persistent object, if it is not in the cache, the object is fetched from the persistent store. The allocation duration of the object is session. If the object is already in the cache, it is returned to the client. The object is locked in the server if a lock option is specified.

This function returns an error for a nonexistent object.

A pin option is used to specify the copy of the object that is to be retrieved:

- If `pin_option` is `OCI_PIN_ANY` (pin any), then if the object is already in the object cache, return this object. Otherwise, the object is retrieved from the database. In this case, it is the same as `OCI_PIN_LATEST`. This option is useful when the client knows that he has the exclusive access to the data in a session.

- If `pin_option` is `OCI_PIN_LATEST` (pin latest), if the object is not locked, it is retrieved from the database. If the object is cached, it is refreshed with the latest version. See `OCIObjectRefresh()` for more information about refreshing. If the object is already pinned in the cache and marked dirty, then a pointer to that object is returned. The object is not refreshed from the database.

- If `pin_option` is `OCI_PIN_RECENT` (pin recent), if the object is loaded into the cache in the current transaction, the object is returned. If the object is not loaded in the current transaction, the object is refreshed from the server.

For Transient Objects
This function returns an error if the transient object has already been freed. This function does not return an error if an exclusive lock is specified in the lock option.

**Related Topics**

- OCIObjectUnpin()
- OCIObjectPinCountReset()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.6.6 OCIObjectPinCountReset()

Completely unpins an object, setting its pin count to zero.

#### Purpose

Completely unpins an object, setting its pin count to zero.

#### Syntax

    sword OCIObjectPinCountReset ( OCIEnv        *env,
                                   OCIError      *err,
                                   void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to an object, which must already be pinned.

#### Comments

This function completely unpins an object, setting its pin count to zero. When an object is completely unpinned, it can be freed implicitly by the OCI at any time without error. The following rules apply to specific object types:

For Persistent Objects
When a persistent object is completely unpinned, it becomes a candidate for aging. The memory of an object is freed when it is aged out. Aging is used to maximize the utilization of memory. A dirty object cannot be aged out unless it is flushed.

For Transient Objects
The pin count of the object is decremented. A transient object can be freed only at the end of its allocation duration or when it is explicitly freed by calling `OCIObjectFree()`.

For Values
This function returns an error for value.

**Related Topics**

- OCIObjectPin()
- OCIObjectUnpin()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIObjectFree()
- [OCIErrorGet()](miscellaneous-functions.md)
- [Pin Count and Unpinning](oci-object-relational-programming.md)

### 27.6.7 OCIObjectPinTable()

Pins a table object for a specified duration.

#### Purpose

Pins a table object for a specified duration.

#### Syntax

    sword OCIObjectPinTable ( OCIEnv             *env,
                              OCIError           *err,
                              const OCISvcCtx    *svc,
                              const OraText      *schema_name,
                              ub4                 s_n_length,
                              const OraText      *object_name,
                              ub4                 o_n_length,
                              const OCIRef       *scope_obj_ref,
                              OCIDuration         pin_duration,
                              void              **object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
The OCI service context handle.

schema_name (IN) \[optional\]
The schema name of the table.

s_n_length (IN) \[optional\]
The length of the schema name indicated in `schema_name`, in bytes.

object_name (IN)
The name of the table.

o_n_length (IN)
The length of the table name specified in `object_name`, in bytes.

scope_obj_ref (IN) \[optional\]
The reference of the scoping object.

pin_duration (IN)
The pin duration.

**See Also:**

`OCIObjectPin()`

<!-- -->

object (OUT)
The pinned table object.

#### Comments

This function pins a table object with the specified pin duration. The client can unpin the object by calling `OCIObjectUnpin()`.

The table object pinned by this call can be passed as a parameter to `OCIObjectNew()` to create a standalone persistent object.

**Note:**

The TDO (array of TDOs or table definition) obtained by this function belongs to the logical partition of the cache corresponding to the service handle (connection) passed in. If TDOs or tables are used across logical partitions, then the behavior is not known and may change between releases.

**Related Topics**

- OCIObjectPin()
- OCIObjectUnpin()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectNew()](oci-miscellaneous-object-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.6.8 OCIObjectUnpin()

Unpins an object.

#### Purpose

Unpins an object.

#### Syntax

    sword OCIObjectUnpin ( OCIEnv        *env,
                           OCIError      *err,
                           void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to an object, which must already be pinned.

#### Comments

There is a pin count associated with each object, which is incremented whenever an object is pinned. When the pin count of the object is zero, the object is said to be completely unpinned. An unpinned object can be freed implicitly by OCI at any time without error.

This function unpins an object. An object is completely unpinned when any of the following is true:

- The object's pin count reaches zero (that is, it is unpinned a total of n times after being pinned a total of n times).

- It is the end of the object's pin duration.

- The function `OCIObjectPinCountReset()` is called on the object.

When an object is completely unpinned, it can be freed implicitly by OCI at any time without error.

The following rules apply to unpinning different types of objects:

For Persistent Objects
When a persistent object is completely unpinned, it becomes a candidate for aging. The memory of an object is freed when it is aged out. Aging is used to maximize the utilization of memory. A dirty object cannot be aged out unless it is flushed.

For Transient Objects
The pin count of the object is decremented. A transient object can be freed only at the end of its allocation duration or when it is explicitly deleted by calling `OCIObjectFree()`.

For Values
This function returns an error for values.

**Related Topics**

- OCIObjectPin()
- OCIObjectPinCountReset()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
