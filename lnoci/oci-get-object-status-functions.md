Lists and describes the OCI get object status functions.

Table 27-7 describes the OCI get object status functions that are described in this section.

Table 27-7 Get Object Status Functions

| Function               | Purpose                                        |
|:-----------------------|:-----------------------------------------------|
| OCIObjectExists()      | Get the existent status of an instance         |
| OCIObjectGetProperty() | Get the status of a particular object property |
| OCIObjectIsDirty()     | Get the dirtied status of an instance          |
| OCIObjectIsLocked()    | Get the locked status of an instance           |

### 27.4.1 OCIObjectExists()

Returns the existence meta-attribute of a standalone instance.

#### Purpose

Returns the existence meta-attribute of a standalone instance.

#### Syntax

    sword OCIObjectExists ( OCIEnv         *env,
                            OCIError       *err,
                            void           *ins,
                            boolean        *exist );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ins (IN)
Pointer to an instance. If it is an object, it must be pinned.

exist (OUT)
Return value for the existence status.

#### Comments

This function returns the existence meta-attribute of an instance. If the instance is a value, this function always returns `TRUE`. The instance must be a standalone persistent or transient object.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [Object Meta-Attributes](oci-object-relational-programming.md)

### 27.4.2 OCIObjectGetProperty()

Retrieves a given property of an object.

#### Purpose

Retrieves a given property of an object.

#### Syntax

    sword OCIObjectGetProperty ( OCIEnv              *envh,
                                 OCIError            *errh,
                                 const void          *obj,
                                 OCIObjectPropId      propertyId,
                                 void                *property,
                                 ub4                 *size );

#### Parameters

envh (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

errh (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

obj (IN)
The object whose property is returned.

propertyId (IN)
The identifier that specifies the property.

property (OUT)
The buffer into which the specified property is copied.

size (IN/OUT)
On input, this parameter specifies the size of the property buffer passed by the caller.

On output, it contains the size in bytes of the property returned. This parameter is required for string-type properties only, such as `OCI_OBJECTPROP_SCHEMA` and `OCI_OBJECTPROP_TABLE`. For non-string properties this parameter is ignored because the size is fixed.

#### Comments

This function returns the specified property of the object. This property is identified by `propertyId`. The property value is copied into `property` and for string typed properties, the string size is returned by `size`.

Objects are classified as persistent, transient, and value depending upon the lifetime and referenceability of the object. Some of the properties are applicable only to persistent objects and some others apply only to persistent and transient objects. An error is returned if the user tries to get a property that is not applicable to the given object. To avoid such an error, first check whether the object is persistent or transient or value (`OCI_OBJECTPROP_LIFETIME` property) and then appropriately query for other properties.

The different property IDs and the corresponding type of `property` argument are given next.

OCI_OBJECTPROP_LIFETIME
This identifies whether the given object is a persistent object or a transient object or a value instance. The `property` argument must be a pointer to a variable of type `OCIObjectLifetime`. Possible values include:

- `OCI_OBJECT_PERSISTENT`

- `OCI_OBJECT_TRANSIENT`

- `OCI_OBJECT_VALUE`

OCI_OBJECTPROP_SCHEMA
This returns the schema name of the table in which the object exists. An error is returned if the given object points to a transient instance or a value. If the input buffer is not big enough to hold the schema name, an error is returned; the error message communicates the required size. Upon success, the size of the returned schema name in bytes is returned by `size`. The `property` argument must be an array of type `text`, and `size` should be set to size of array in bytes by the caller.

OCI_OBJECTPROP_TABLE
This returns the table name in which the object exists. An error is returned if the given object points to a transient instance or a value. If the input buffer is not big enough to hold the table name, an error is returned; the error message communicates the required size. Upon success, the size of the returned table name in bytes is returned by `size`. The `property` argument must be an array of type `text`, and `size` should be set to size of array in bytes by the caller.

OCI_OBJECTPROP_PIN_DURATION
This returns the pin duration of the object. An error is returned if the given object points to a value instance. The `property` argument must be a pointer to a variable of type `OCIDuration`. Valid values include:

- `OCI_DURATION_SESSION`

- `OCI_DURATION_TRANS`

For more information about durations, see [Object Duration](object-advanced-topics-in-oci.md).

OCI_OBJECTPROP_ALLOC_DURATION
This returns the allocation duration of the object. The `property` argument must be a pointer to a variable of type `OCIDuration`. Valid values include:

- `OCI_DURATION_SESSION`

- `OCI_DURATION_TRANS`

For more information about durations, see [Object Duration](object-advanced-topics-in-oci.md).

OCI_OBJECTPROP_LOCK
This returns the lock status of the object. The possible lock statuses are enumerated by `OCILockOpt`. An error is returned if the given object points to a transient or value instance. The `property` argument must be a pointer to a variable of type `OCILockOpt`. The lock status of an object can also be retrieved by calling `OCIObjectIsLocked()`. Valid values include:

- `OCI_LOCK_NONE` (no lock)

- `OCI_LOCK_X` (exclusive lock)

- `OCI_LOCK_X_NOWAIT` (exclusive lock with the `NOWAIT` option)

  **See Also:**

  [About Locking with the NOWAIT Option](object-advanced-topics-in-oci.md)

OCI_OBJECTPROP_MARKSTATUS
This returns the dirty status and indicates whether the object is a new object, updated object, or deleted object. An error is returned if the given object points to a transient or value instance. The `property` argument must be of type `OCIObjectMarkStatus`. Valid values include:

- `OCI_OBJECT_NEW`

- `OCI_OBJECT_DELETED`

- `OCI_OBJECT_UPDATED`

The following macros are available to test the object mark status:

- `OCI_OBJECT_IS_UPDATED` (flag)

- `OCI_OBJECT_IS_DELETED` (flag)

- `OCI_OBJECT_IS_NEW` (flag)

- `OCI_OBJECT_IS_DIRTY` (flag)

OCI_OBJECTPROP_VIEW
This identifies whether the specified object is a view object or not. If the property value returned is `TRUE`, the object is a view; otherwise, it is not. An error is returned if the given object points to a transient or value instance. The `property` argument must be of type `boolean`.

**Related Topics**

- [OCIObjectLock()](oci-miscellaneous-object-functions.md)
- [OCIObjectMarkDelete()](oci-mark-or-unmark-object-cache-functions.md)
- [OCIObjectMarkUpdate()](oci-mark-or-unmark-object-cache-functions.md)
- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIObjectIsLocked()
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.4.3 OCIObjectIsDirty()

Checks to see if an object is marked as dirty.

#### Purpose

Checks to see if an object is marked as dirty.

#### Syntax

    sword OCIObjectIsDirty ( OCIEnv       *env,
                             OCIError     *err,
                             void         *ins,
                             boolean      *dirty );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ins (IN)
Pointer to an instance.

dirty (OUT)
Return value for the dirty status.

#### Comments

The instance passed to this function must be standalone. If the instance is an object, the instance must be pinned.

This function returns the dirty status of an instance. If the instance is a value, this function always returns `FALSE` for the dirty status.

**Related Topics**

- [OCIObjectMarkUpdate()](oci-mark-or-unmark-object-cache-functions.md)
- OCIObjectGetProperty()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.4.4 OCIObjectIsLocked()

Gets lock status of an object.

#### Purpose

Gets lock status of an object.

#### Syntax

    sword OCIObjectIsLocked ( OCIEnv       *env,
                              OCIError     *err,
                              void         *ins,
                              boolean      *lock );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ins (IN)
Pointer to an instance. The instance must be standalone, and if it is an object, it must be pinned.

lock (OUT)
Return value for the lock status.

#### Comments

This function returns the lock status of an instance. If the instance is a value, this function always returns `FALSE`.

**Related Topics**

- [OCIObjectLock()](oci-miscellaneous-object-functions.md)
- OCIObjectGetProperty()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
