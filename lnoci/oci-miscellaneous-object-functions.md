Lists and describes the miscellaneous object functions.

Table 27-8 describes the miscellaneous object functions that are described in this section.

Table 27-8 Miscellaneous Object Functions

| Function                | Purpose                                               |
|:------------------------|:------------------------------------------------------|
| OCIObjectCopy()         | Copy one instance to another                          |
| OCIObjectGetAttr()      | Get an object attribute                               |
| OCIObjectGetInd()       | Get `NULL` structure of an instance                   |
| OCIObjectGetObjectRef() | Return reference to a given object                    |
| OCIObjectGetTypeRef()   | Get a reference to a TDO of an instance               |
| OCIObjectLock()         | Lock a persistent object                              |
| OCIObjectLockNoWait()   | Lock a persistent object but do not wait for the lock |
| OCIObjectNew()          | Create a new instance                                 |
| OCIObjectSetAttr()      | Set an object attribute                               |

### 27.5.1 OCIObjectCopy()

Copies a source instance to a destination.

#### Purpose

Copies a source instance to a destination.

#### Syntax

    sword OCIObjectCopy ( OCIEnv              *env,
                          OCIError            *err,
                          const OCISvcCtx     *svc,
                          void                *source,
                          void                *null_source,
                          void                *target,
                          void                *null_target,
                          OCIType             *tdo,
                          OCIDuration          duration,
                          ub1                  option );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
An OCI service context handle, specifying the service context on which the copy operation is occurring.

source (IN)
A pointer to the source instance; if it is an object, it must be pinned.

**See Also:**

`OCIObjectPin()`

<!-- -->

null_source (IN)
Pointer to the `NULL` structure of the source object.

target (IN)
A pointer to the target instance; if it is an object, it must be pinned.

null_target (IN)
A pointer to the `NULL` structure of the target object.

tdo (IN)
The TDO for both the source and the target. Can be retrieved with `OCIDescribeAny()`.

duration (IN)
Allocation duration of the target memory.

option (IN)
This parameter is currently unused. Pass as zero or `OCI_DEFAULT`.

#### Comments

This function copies the contents of the `source` instance to the `target` instance. This function performs a deep copy such that all of the following information is copied:

- All the top-level attributes (see the exceptions later)

- All secondary memory (of the source) reachable from the top-level attributes

- The `NULL` structure of the instance

Memory is allocated with the duration specified in the `duration` parameter.

Certain data items are not copied, such as, if the attribute is an internal LOB, then only the LOB locator from the source object is copied. A copy of the LOB data is not made until `OCIObjectFlush()` is called. Before the target object is flushed, both the source and the target locators refer to the same LOB value.

The target or the containing instance of the target must have been created. This can be done with `OCIObjectNew()` or `OCIObjectPin()` depending on whether the target object exists.

The `source` and `target` instances must be of the same type. If the source and target are located in different databases, then the same type must exist in both databases.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIObjectFlush()](oci-flush-or-refresh-functions.md)
- OCIObjectNew()
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.5.2 OCIObjectGetAttr()

Retrieves an object attribute.

#### Purpose

Retrieves an object attribute.

#### Syntax

    sword OCIObjectGetAttr ( OCIEnv             *env,
                             OCIError           *err,
                             void               *instance,
                             void               *null_struct,
                             struct OCIType     *tdo,
                             const OraText      **names,
                             const ub4          *lengths,
                             const ub4           name_count,
                             const ub4          *indexes,
                             const ub4           index_count,
                             OCIInd             *attr_null_status,
                             void              **attr_null_struct,
                             void              **attr_value,
                             struct OCIType    **attr_tdo );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
Pointer to an object.

null_struct (IN)
The `NULL` structure of the object or array.

tdo (IN)
Pointer to the type descriptor object (TDO).

names (IN)
Array of attribute names. This is used to specify the names of the attributes in the path expression.

lengths (IN)
Array of lengths of attribute names, in bytes.

name_count (IN)
Number of elements in the array `names`.

indexes (IN) \[optional\]
Not currently supported. Pass as `(ub4 *)0`.

index_count (IN) \[optional\]
Not currently supported. Pass as `(ub4)0`.

attr_null_status (OUT)
The `NULL` status of the attribute if the type of attribute is primitive.

attr_null_struct (OUT)
This parameter is filled only for object and opaque attributes, not for collections. For collections (pass `OCICollGetElem`), `attr_null_struct` is `NULL`. For collections, this parameter indicates if the entire collection is `NULL` or not.

attr_value (OUT)
Pointer to the attribute value. See

[Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `attr_value` after this call completes successfully.

attr_tdo (OUT)
Pointer to the TDO of the attribute.

#### Comments

This function gets a value from an object. The position of the attribute returned is specified as a path expression, which is an array of names and an array of indexes. If the parameter `instance `points to an object, then the path expression specifies the location of the attribute in the object. It is assumed that the object is pinned and that the value returned is valid until the object is unpinned. The values returned are considered read-only and should not be modified in any way.

If both `attr_null_status` and `attr_null_struct` are `NULL`, no `NULL` information is returned.

#### Example

For the path expression stanford.cs.stu\[5\].addr, the arrays appear as:

names = {"stanford", "cs", "stu", "addr"}

lengths = {8, 2, 3, 4}

indexes = {5}

**Related Topics**

- OCIObjectSetAttr()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.5.3 OCIObjectGetInd()

Retrieves the `NULL` indicator structure of a standalone instance.

#### Purpose

Retrieves the `NULL` indicator structure of a standalone instance.

#### Syntax

    sword OCIObjectGetInd ( OCIEnv        *env,
                            OCIError      *err,
                            void          *instance,
                            void         **null_struct );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
A pointer to the instance whose `NULL` structure is being retrieved. The instance must be standalone. If `instance` is an object, it must already be pinned.

null_struct (OUT)
The `NULL` indicator structure for the instance.

**See Also:**

[NULL Indicator Structure](oci-object-relational-programming.md) for a discussion of the NULL indicator structure and examples of its use

#### Comments

None.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.5.4 OCIObjectGetObjectRef()

Returns a reference to a given persistent object.

#### Purpose

Returns a reference to a given persistent object.

#### Syntax

    sword OCIObjectGetObjectRef ( OCIEnv        *env,
                                  OCIError      *err,
                                  void          *object,
                                  OCIRef        *object_ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
Pointer to a persistent object. It must already be pinned.

object_ref (OUT)
A reference to the object specified in `object`. The reference must already be allocated. This can be accomplished with `OCIObjectNew()`.

#### Comments

This function returns a reference to the given persistent object, when given a pointer to the object. Passing a value (rather than an object) to this function causes an error.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [Object Meta-Attributes](oci-object-relational-programming.md)

### 27.5.5 OCIObjectGetTypeRef()

Returns a reference to the type descriptor object (TDO) of a standalone instance.

#### Purpose

Returns a reference to the type descriptor object (TDO) of a standalone instance.

#### Syntax

    sword OCIObjectGetTypeRef ( OCIEnv        *env,
                                OCIError      *err,
                                void          *instance,
                                OCIRef        *type_ref );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
A pointer to the standalone instance. It must be standalone, and if it is an object, it must already be pinned.

type_ref (OUT)
A reference to the type of the object. The reference must already be allocated. This can be accomplished with `OCIObjectNew()`.

#### Comments

None.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIObjectNew()
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.5.6 OCIObjectLock()

Locks a persistent object at the server.

#### Purpose

Locks a persistent object at the server.

#### Syntax

    sword OCIObjectLock ( OCIEnv        *env,
                          OCIError      *err,
                          void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to the persistent object being locked. It must already be pinned.

#### Comments

This function returns an error for transient objects and values. It also returns an error if the object does not exist.

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectIsLocked()](oci-get-object-status-functions.md)
- [OCIObjectGetProperty()](oci-get-object-status-functions.md)
- OCIObjectLockNoWait()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Locking Objects for Update](object-advanced-topics-in-oci.md)

### 27.5.7 OCIObjectLockNoWait()

Locks a persistent object at the server but does not wait for the lock.

#### Purpose

Locks a persistent object at the server but does not wait for the lock. Returns an error if the lock is unavailable.

#### Syntax

    sword OCIObjectLockNoWait ( OCIEnv        *env,
                                OCIError      *err,
                                void          *object );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

object (IN)
A pointer to the persistent object being locked. It must already be pinned.

#### Comments

This function locks a persistent object at the server. However, unlike `OCIObjectLock()`, this function does not wait if another user holds the lock on the object and an error is returned if the object is currently locked by another user. This function also returns an error for transient objects and values, or objects that do not exist.

The lock of an object is released at the end of a transaction.

`OCIObjectLockNoWait()` returns the following values:

- `OCI_INVALID_HANDLE`, if the environment handle or error handle is `NULL`

- `OCI_SUCCESS`, if the operation succeeds

- `OCI_ERROR`, if the operation fails

**Related Topics**

- [OCIObjectPin()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectIsLocked()](oci-get-object-status-functions.md)
- [OCIObjectGetProperty()](oci-get-object-status-functions.md)
- OCIObjectLock()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
- [About Locking Objects for Update](object-advanced-topics-in-oci.md)

### 27.5.8 OCIObjectNew()

Creates a standalone instance.

#### Purpose

Creates a standalone instance.

#### Syntax

    sword OCIObjectNew ( OCIEnv            *env,
                         OCIError          *err,
                         const OCISvcCtx   *svc,
                         OCITypeCode        typecode,
                         OCIType           *tdo,
                         void              *table,
                         OCIDuration        duration,
                         boolean            value,
                         void             **instance );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. The handle can be initialized in UTF-16 (Unicode) mode. See the description of `OCIEnvNlsCreate()`.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

svc (IN)
OCI service handle.

typecode (IN)
The typecode of the type of the instance.

**See Also:**

[Typecodes](data-types.md)

<!-- -->

tdo (IN) \[optional\]
Pointer to the type descriptor object. The TDO describes the type of the instance that is to be created. See `OCITypeByName()` for obtaining a TDO. The TDO is required for creating a named type, such as an object or a collection.

table (IN) \[optional\]
Pointer to a table object that specifies a table in the server. `This` parameter can be set to `NULL` if no table is given. See the following description to learn how the table object and the TDO are used together to determine the kind of instances (persistent, transient, value) to be created. Also see `OCIObjectPinTable()` for retrieving a table object.

duration (IN)
This is an overloaded parameter. The use of this parameter is based on the kind of the instance that is to be created. See Table 27-9 for more information.

- For a persistent object type of instance, this parameter specifies the pin duration.

- For a transient object type of instance, this parameter specifies the allocation duration and pin duration.

- For a value type of instance, this parameter specifies the allocation duration.

value (IN)
Specifies whether the created object is a value. If `TRUE`, then a value is created. Otherwise, a referenceable object is created. If the instance is not an object, then this parameter is ignored.

instance (OUT)
Address of the newly created instance. The instance can be a character string in UTF-16 (Unicode) if the environment handle has the appropriate setting and the object is `OCIString`.

#### Comments

This function creates a new instance of the type specified by the typecode or the TDO. The type can be complex or primitive.

For Records
When creating a package record type using `OCIObjectNew()`, clients must use typecode `OCI_TYPECODE_RECORD` when instantiating a record type.

Records are allocated in the allocation duration specified in `OCIObjectNew()`. They are subsequently freed at the end of that duration.

Record field initializers are not supported for records instantiated on the client. For instance, given the following mypack package definition, the following error is returned when you resolve it using `OCITypeByFullName()`: `OCI-22352: Type is unsupported or contains an unsupported attribute or element`. (Thus, you will never even get to call `OCIObjectNew()`).

    create or replace package mypack is
      type r is record (rec_field number := 10);
    end;

All records are null activated; that is, all fields of an instantiated record are set to `NULL`. In keeping with PL/SQL null semantics, all instantiated records are also atomically not-`NULL`.

For Collections
When creating a new instance of a package collection type, the `value` parameter must be `TRUE`. This is because package collection types cannot be persistent or referenceable, and so they must always be instantiated as values. Calling `OCIObjectNew()` for a package collection type with a `FALSE` value parameter results in an error.

Package collections are allocated in the allocation duration specified in `OCIObjectNew()`. They are subsequently freed at the end of that duration.

When creating a package, clients can use the typecodes as follows:

- `OCI_TYPECODE_NAMEDCOLLECTION` for schema level collections and package collection types

- `OCI_TYPECODE_ITABLE` for index tables

- `OCI_TYPECODE_TABLE` for nested tables

- `OCI_TYPECODE_VARRAY` for varrays

For Booleans
When creating new Boolean types, clients should use `OCI_TYPECODE_BOOLEAN`.

OCI String Objects
It can create an OCIString object with a Unicode buffer if the typecode indicates the object to be created is `OCIString`.

**See Also:**

[Typecodes](data-types.md)

Table 27-9 shows that based on the parameters `typecode` (or `tdo`), `value`, and `table`, different instances are created.

Table 27-9 Instances Created

| Type of the Instance        | Table != NULL     | Table == NULL    |
|:----------------------------|:------------------|:-----------------|
| object type (value=`TRUE`)  | value             | value            |
| object type (value=`FALSE`) | persistent object | transient object |
| built-in type               | value             | value            |
| collection type             | value             | value            |

This function allocates the top-level memory chunk of an instance. The attributes in the top-level memory are initialized, which means that an attribute of `VARCHAR2` is initialized to an `OCIString` of 0 length. If the instance is an object, the object is marked existent but is atomically `NULL`.

**See Also:**

[Create Objects Based on Object Views and Object Tables with Primary-Key-Based OIDs](oci-object-relational-programming.md) for information about creating new objects based on object views or user-created OIDs

<!-- -->

For Persistent Objects
The object is marked dirty and existent. The allocation duration for the object is session. The object is pinned, and the pin duration is specified by the given parameter `duration`. Creating a persistent object does not cause any entries to be made into a database table until the object is flushed to the server.

For Transient Objects
The object is pinned. The allocation duration and the pin duration are specified by the given parameter `duration`.

For Values
The allocation duration is specified by the given parameter `duration`.

#### Attribute Values of New Objects

By default, all attributes of a newly created object have `NULL` values. After initializing attribute data, the user must change the corresponding `NULL` status of each attribute to non-`NULL`.

It is possible to have attributes set to non-`NULL` values when an object is created. This is accomplished by setting the `OCI_ATTR_OBJECT_NEWNOTNULL` attribute of the environment handle to `TRUE` using `OCIAttrSet()`. This mode can later be turned off by setting the attribute to `FALSE`. If `OCI_ATTR_OBJECT_NEWNOTNULL` is set to `TRUE`, then `OCIObjectNew()` creates a non-`NULL` object.

**See Also:**

[Attribute Values of New Objects](oci-object-relational-programming.md)

#### Objects with LOB Attributes

If the object contains an internal LOB attribute, the LOB is set to empty. The object must be marked as dirty and flushed (to insert the object into the table) and repinned before the user can start writing data into the LOB. When pinning the object after creating it, you must use the `OCI_PIN_LATEST` pin option to retrieve the newly updated LOB locator from the server.

If the object contains an external LOB attribute (FILE), the FILE locator is allocated but not initialized. The user must call `OCILobFileSetName()` to initialize the FILE attribute before flushing the object to the database. It is an error to perform an `INSERT` or `UPDATE` operation on a FILE without first indicating a directory object and file name. Once the file name is set, the user can start reading from the FILE.

**Note:**

Oracle Database supports only binary FILEs (`BFILEs`).

**Related Topics**

- [OCIObjectPinTable()](oci-pin-unpin-and-free-functions.md)
- [OCIObjectFree()](oci-pin-unpin-and-free-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCITypeByName()](oci-type-information-accessor-functions.md)
- [OCILobFileSetName()](lob-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 27.5.9 OCIObjectSetAttr()

Sets an object attribute.

#### Purpose

Sets an object attribute.

#### Syntax

    sword OCIObjectSetAttr ( OCIEnv              *env,
                             OCIError            *err,
                             void                *instance,
                             void                *null_struct,
                             struct OCIType      *tdo,
                             const OraText       **names,
                             const ub4           *lengths,
                             const ub4            name_count,
                             const ub4           *indexes,
                             const ub4            index_count,
                             const OCIInd         attr_null_status,
                             const void          *attr_null_struct,
                             const void          *attr_value );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

instance (IN)
Pointer to an object instance.

null_struct (IN)
The `NULL` structure of the object instance or array.

tdo (IN)
Pointer to the TDO.

names (IN)
Array of attribute names. This is used to specify the names of the attributes in the path expression.

lengths (IN)
Array of lengths of attribute names, in bytes.

name_count (IN)
Number of elements in the array `names`.

indexes (IN) \[optional\]
Not currently supported. Pass as `(ub4 *)0`.

index_count (IN) \[optional\]
Not currently supported. Pass as `(ub4)0`.

attr_null_status (IN)
The `NULL` status of the attribute if the type of attribute is primitive.

attr_null_struct (IN)
The `NULL` structure of an object or collection attribute.

attr_value (IN)
Pointer to the attribute value. See [Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `attr_value` after this call completes successfully. Note that the given element is deep copied, and `attr_value` is strictly an input parameter.

#### Comments

This function sets the attribute of the given object with the given value. The position of the attribute is specified as a path expression, which is an array of names and an array of indexes.

#### Example

For the path expression stanford.cs.stu\[5\].addr, the arrays appear as:

names = {"stanford", "cs", "stu", "addr"}

lengths = {8, 2, 3, 4}

indexes = {5}

**Related Topics**

- OCIObjectGetAttr()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
