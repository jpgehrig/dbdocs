Lists and describes the OCI mark or unmark object and cache functions.

Table 27-6 describes the OCI mark or unmark object and cache functions that are described in this section.

Table 27-6 Mark or Unmark Object and Cache Functions

| Function                   | Purpose                                             |
|:---------------------------|:----------------------------------------------------|
| OCICacheUnmark()           | Unmark objects in the cache                         |
| OCIObjectMarkDelete()      | Mark an object deleted or delete a value instance   |
| OCIObjectMarkDeleteByRef() | Mark an object deleted when given a reference to it |
| OCIObjectMarkUpdate()      | Mark an object as updated or dirty                  |
| OCIObjectUnmark()          | Unmark an object                                    |
| OCIObjectUnmarkByRef()     | Unmark an object, when given a reference to it      |

### 27.3.1 OCICacheUnmark()

Unmarks all dirty objects in the object cache.

#### Purpose

Unmarks all dirty objects in the object cache.

#### Syntax

    sword OCICacheUnmark ( OCIEnv            *env,
                           OCIError          *err,
                           const OCISvcCtx   *svc );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service context.

#### Comments

If a connection is specified, this function unmarks all dirty objects in that connection. Otherwise, all dirty objects in the cache are unmarked.

**Related Topics**

- OCIObjectUnmark()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

`OCIObjectUnmark()` for more information about unmarking an object

### 27.3.2 OCIObjectMarkDelete()

Marks a standalone instance as deleted, when given a pointer to the instance.

#### Purpose

Marks a standalone instance as deleted, when given a pointer to the instance.

#### Syntax

    sword OCIObjectMarkDelete ( OCIEnv        *env,
                                OCIError      *err,
                                void          *instance );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
Pointer to the instance. It must be standalone, and if it is an object, it must be pinned.

#### Comments

This function accepts a pointer to a standalone instance and marks the object as deleted. The object is freed according to the following rules:

For Persistent Objects
The object is marked deleted. The memory of the object is not freed. The object is deleted in the server when the object is flushed.

For Transient Objects
The object is marked deleted. The memory of the object is not freed.

For Values
This function frees a value immediately.

**Related Topics**

- OCIObjectMarkDeleteByRef()
- [OCIObjectGetProperty()](oci-get-object-status-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.3.3 OCIObjectMarkDeleteByRef()

Marks an object as deleted, when given a reference to the object.

#### Purpose

Marks an object as deleted, when given a reference to the object.

#### Syntax

    sword OCIObjectMarkDeleteByRef ( OCIEnv         *env,
                                     OCIError       *err,
                                     OCIRef         *object_ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object_ref (IN)
Reference to the object to be deleted.

#### Comments

This function accepts a reference to an object, and marks the object designated by `object_ref `as deleted. The object is marked and freed as follows:

For Persistent Objects
If the object is not loaded, then a temporary object is created and is marked deleted. Otherwise, the object is marked deleted.

The object is deleted in the server when the object is flushed.

For Transient Objects
The object is marked deleted. The object is not freed until it is unpinned.

**Related Topics**

- OCIObjectMarkDelete()
- [OCIObjectGetProperty()](oci-get-object-status-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.3.4 OCIObjectMarkUpdate()

Marks a persistent object as updated (dirty).

#### Purpose

Marks a persistent object as updated (dirty).

#### Syntax

    sword OCIObjectMarkUpdate ( OCIEnv        *env,
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

This function marks a persistent object as updated (dirty). The following special rules apply to different types of objects. The dirty status of an object can be checked by calling `OCIObjectIsLocked()`.

For Persistent Objects
This function marks the specified persistent object as updated.

When the object cache is flushed, it writes the persistent objects to the server. The object is not locked or flushed by this function. It is an error to update a deleted object.

After an object is marked updated and flushed, this function must be called again to mark the object as updated if it has been dirtied after being flushed.

For Transient Objects
This function marks the specified transient object as updated. The transient objects are not written to the server. It is an error to update a deleted object.

For Values
This function has no effect on values.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectGetProperty()](oci-get-object-status-functions.md)
- [OCIObjectIsDirty()](oci-get-object-status-functions.md)
- OCIObjectUnmark()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectIsLocked()](oci-get-object-status-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Marking Objects and Flushing Changes](oci-object-relational-programming.md)

### 27.3.5 OCIObjectUnmark()

Unmarks an object as dirty.

#### Purpose

Unmarks an object as dirty.

#### Syntax

    sword OCIObjectUnmark ( OCIEnv       *env,
                            OCIError     *err,
                            void         *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
Pointer to the persistent object. It must be pinned.

#### Comments

For Persistent Objects and Transient Objects
This function unmarks the specified persistent object as dirty. Changes that are made to the object are not written to the server. If the object is marked as locked, it remains marked as locked. The changes that have already been made to the object are not undone implicitly.

For Values
This function has no effect if called on a value.

**Related Topics**

- OCIObjectUnmarkByRef()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.3.6 OCIObjectUnmarkByRef()

Unmarks an object as dirty, when given a `ref` to the object.

#### Purpose

Unmarks an object as dirty, when given a `ref` to the object.

#### Syntax

    sword OCIObjectUnmarkByRef ( OCIEnv      *env,
                                 OCIError    *err,
                                 OCIRef      *ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

ref (IN)
Reference of the object. It must be pinned.

#### Comments

This function unmarks an object as dirty. This function is identical to `OCIObjectUnmark()`, except that it takes a `ref` to the object as an argument.

For Persistent Objects and Transient Objects
This function unmarks the specified persistent object as dirty. Changes that are made to the object are not written to the server. If the object is marked as locked, it remains marked as locked. The changes that have already been made to the object are not undone implicitly.

For Values
This function has no effect on values.

**Related Topics**

- OCIObjectUnmark()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
