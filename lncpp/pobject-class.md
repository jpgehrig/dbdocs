OCCI provides object navigational calls that enable applications to perform any of the following on objects:

- Creating, accessing, locking, deleting, copying, and flushing objects

- Getting references to the objects

This class enables the type definer to specify when a class can have persistent or transient instances. Instances of classes derived from `PObject` are either persistent or transient. For example, class `A` that is persistent-capable inherits from the `PObject` class:

    class A : PObject { ... }

The only methods valid on a `NULL` `PObject` are [setName()](bfile-class.md), isNull(), and operator=().

Some methods, such as lock(), apply only for persistent instances, not for transient instances.

Table 13-31 Enumerated Values Used by PObject Class

| Attribute     | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LockOption`  | • `OCCI_LOCK_WAIT` instructs the cache to pin the object only after acquiring a lock; if the object is locked by another user, the pin call with this option waits until it can acquire the lock before returning to the caller; equivalent to `SELECT FOR UPDATE`<br>• `OCCI_LOCK_NOWAIT` instructs the cache to pin the object only after acquiring a lock; does not wait if the object is currently locked by another user; equivalent to `SELECT FOR UPDATE WITH NOWAIT` |
| `UnpinOption` | • `OCCI_PINCOUNT_RESET` resets the object's pin count to `0`<br>• `OCCI_PINCOUNT_DECR` decrements the object's pin count by `1`                                                                                                                                                                                                                                                                                                                                              |

Table 13-32 Summary of PObject Methods

| Method            | Summary                                                                                                     |
|:------------------|:------------------------------------------------------------------------------------------------------------|
| PObject()         | `PObject` class constructor.                                                                                |
| flush()           | Flushes a modified persistent object to the database server.                                                |
| getConnection()   | Returns the connection from which the `PObject` object was instantiated.                                    |
| getRef()          | Returns a reference to a given persistent object.                                                           |
| getSQLTypeName()  | Returns the Oracle database typename for this class.                                                        |
| isLocked()        | Tests whether the persistent object is locked.                                                              |
| isNull()          | Tests whether the object is `NULL`.                                                                         |
| lock()            | Lock a persistent object on the database server. The default mode is to wait for the lock if not available. |
| markDelete()      | Marks a persistent object as deleted.                                                                       |
| markModified()    | Marks a persistent object as modified or dirty.                                                             |
| operator=()       | Assigns one `PObject` to another.                                                                           |
| operator delete() | Remove the persistent object from the application cache only.                                               |
| operator new()    | Creates a new persistent / transient instance.                                                              |
| pin()             | Pins an object.                                                                                             |
| setNull()         | Sets the object value to `NULL`.                                                                            |
| unmark()          | Unmarks an object as dirty.                                                                                 |
| unpin()           | Unpins an object. In the default mode, the pin count of the object is decremented by one.                   |

### 13.23.1 PObject()

`PObject` class constructor.

| Syntax                                  | Description                  |
|:----------------------------------------|:-----------------------------|
| `PObject();`                            | Creates a `NULL PObject.`    |
| `PObject(`<br>`   const PObject &obj);` | Creates a copy of `PObject.` |

| Parameter | Description        |
|:----------|:-------------------|
| `obj`     | The source object. |

### 13.23.2 flush()

This method flushes a modified persistent object to the database server.

#### Syntax

    void flush();

### 13.23.3 getConnection()

Returns the connection from which the persistent object was instantiated.

#### Syntax

    const Connection *getConnection() const;

### 13.23.4 getRef()

This method returns a reference to the persistent object.

#### Syntax

    RefAny getRef() const;

### 13.23.5 getSQLTypeName()

Returns the Oracle database typename for this class.

#### Syntax

    string getSQLTypeName() const;

### 13.23.6 isLocked()

This method test whether the persistent object is locked. If the persistent object is locked, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isLocked() const;

### 13.23.7 isNull()

This method tests whether the persistent object is `NULL`. If the persistent object is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.23.8 lock()

Locks a persistent object on the database server.

#### Syntax

    void lock(
       PObject::LockOption lock_option);

| Parameter     | Description                       |
|:--------------|:----------------------------------|
| `lock_option` | Locking options; see Table 13-31. |

### 13.23.9 markDelete()

This method marks a persistent object as deleted.

#### Syntax

    void markDelete();

### 13.23.10 markModified()

This method marks a persistent object as modified or dirty.

#### Syntax

    void mark_Modified();

### 13.23.11 operator=()

This method assigns the value of a persistent object this `PObject` object. The nature (transient or persistent) of the object is maintained. `NULL` information is copied from the source instance.

#### Syntax

    PObject& operator=(
       const PObject& obj);

| Parameter | Description                                           |
|:----------|:------------------------------------------------------|
| `obj`     | The object from which the assigned value is obtained. |

### 13.23.12 operator delete()

Deletes a persistent or transient object. The delete operator on a persistent object removes the object from the application cache only. To delete the object from the database server, invoke the markDelete() method.

#### Syntax

    void operator delete(
       void *obj,
       size_t size);

| Parameter | Description                                            |
|:----------|:-------------------------------------------------------|
| `obj`     | The pointer to object to be deleted                    |
| `size`    | (Optional) Size is implicitly obtained from the object |

### 13.23.13 operator new()

This method creates a new object. A persistent object is created if the connection and table name are provided. Otherwise, a transient object is created.

| Syntax                                                                                                                                                                                                                        | Description                                                                            |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------|
| `void *operator new(`<br>`   size_t size);`                                                                                                                                                                                   | Creates a default new object, with a size specification only                           |
| `void *operator new(`<br>`   size_t size,`<br>`   const Connection *conn,`<br>`   const string& tableName,`<br>`   const char *typeName);`                                                                                    | Used for creating transient objects when client side characterset is multibyte.        |
| `void *operator new(`<br>`   size_t size,`<br>`   const Connection *conn,`<br>`   const string& tableName,`<br>`   const string& typeName,`<br>`   const string& schTableName="",`<br>`   const string& schTypeName="");`     | Used for creating persistent objects when client side characterset is multibyte.       |
| `void *operator new(`<br>`   size_t size,`<br>`   const Connection *conn,`<br>`   const UString& tableName,`<br>`   const UString& typeName,`<br>`   const UString& schTableName="",`<br>`   const UString& schTypeName="");` | Used for creating persistent objects when client side characterset is unicode (UTF16). |

| Parameter      | Description                                                                                 |
|:---------------|:--------------------------------------------------------------------------------------------|
| `size`         | size of the object                                                                          |
| `conn`         | The connection to the database in which the persistent object is to be created.             |
| `tableName`    | The name of the table in the database server.                                               |
| `typeName`     | The SQL type name corresponding to this C++ class. The format is `<schemaname>.<typename>`. |
| `schTableName` | The schema table name.                                                                      |
| `schTypeName`  | The schema type name.                                                                       |

### 13.23.14 pin()

This method pins the object and increments the pin count by one. If the object is pinned, it is not freed by the cache even if there are no references to this object instance.

#### Syntax

    void pin();

### 13.23.15 setNull()

This method sets the object value to `NULL`.

#### Syntax

    void setNull();

### 13.23.16 unmark()

This method unmarks a persistent object as modified or deleted.

#### Syntax

    void unmark();

### 13.23.17 unpin()

This method unpins a persistent object. In the default mode, the pin count of the object is decremented by one. When this method is invoked with `OCCI_PINCOUNT_RESET`, the pin count of the object is reset. If the pin count is reset, this method invalidates all the references (`Ref`s) pointing to this object. The cache sets the object eligible to be freed, if necessary, reclaiming memory.

#### Syntax

    void unpin(
       UnpinOption mode=OCCI_PINCOUNT_DECR);

| Parameter | Description                                                                                                                                                                          |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mode`    | Specifies whether the `UnpinOption` mode, or the pin count, should be decremented or reset to `0`. See Table 13-31. Valid values are `OCCI_PINCOUNT_RESET` and `OCCI_PINCOUNT_DECR`. |
