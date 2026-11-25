The mapping in the C++ programming language of an SQL REF value, which is a reference to an SQL structured type value in the database.

Each REF value has a unique identifier of the object it refers to. An SQL REF value may be used instead of the SQL structured type it references; it may be used as either a column value in a table or an attribute value in a structured type.

Because an SQL REF value is a logical pointer to an SQL structured type, a Ref object is by default also a logical pointer; thus, retrieving an SQL REF value as a Ref object does not materialize the attributes of the structured type on the client.

The only methods valid on a `NULL` `Ref` object are isNull(), and operator=().

A Ref object can be saved to persistent storage and is de-referenced through operator\*(), operator-\>() or ptr() methods. T must be a class derived from `PObject`. In the following sections, `T*` and `PObject`\* are used interchangeably.

Table 13-35 Enumerated Values Used by Ref Class

| Attribute        | Options                                                                                                                                                                                                                                                                                                                                            |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LockOptions`    | • `OCCI_LOCK_NONE` clears the lock setting on the `Ref` object.<br>• `OCCI_LOCK_X` indicates that the object should be locked, and to wait for the lock to be available if the object is locked by another session.<br>• `OCCI_LOCK_X_NOWAIT` indicates that the object should be locked, and returns an error if it is locked by another session. |
| `PrefetchOption` | • `OCCI_MAX_PREFETCH_DEPTH` indicates that the fetch should be done to maximum depth.                                                                                                                                                                                                                                                              |

Table 13-36 Summary of Ref Methods

| Method          | Summary                                                                                               |
|:----------------|:------------------------------------------------------------------------------------------------------|
| Ref()           | `Ref` object constructor.                                                                             |
| clear()         | Clears the reference.                                                                                 |
| getConnection() | Returns the connection this ref was created from.                                                     |
| isClear()       | Checks if the Ref is cleared.                                                                         |
| isNull()        | Checks if the `Ref` is `NULL`.                                                                        |
| markDelete()    | Marks the referred object as deleted.                                                                 |
| operator-\>()   | Dereferences the `Ref` and pins the object if necessary.                                              |
| operator\*()    | Dereferences the `Ref` and pins or fetches the object if necessary.                                   |
| operator==()    | Checks if the `Ref` and the pointer refer to the same object.                                         |
| operator!=()    | Checks if the `Ref` and the pointer refer to different objects.                                       |
| operator=()     | Assignment operator.                                                                                  |
| ptr()           | Returns a pointer to a `PObject`. Dereferences the `Ref` and pins or fetches the object if necessary. |
| setLock()       | Sets the lock option for the object referred from this.                                               |
| setNull()       | Sets the Ref to `NULL`.                                                                               |
| setPrefetch()   | Sets the prefetch options for complex object retrieval.                                               |
| unmarkDelete()  | Unmarks for delete the object referred by this.                                                       |

### 13.25.1 Ref()

`Ref` object constructor.

| Syntax                             | Description              |
|:-----------------------------------|:-------------------------|
| `Ref();`                           | Creates a `NULL Ref.`    |
| `Ref(`<br>`   const Ref<T> &src);` | Creates a copy of `Ref.` |

| Parameter | Description                     |
|:----------|:--------------------------------|
| `src`     | The `Ref` that is being copied. |

### 13.25.2 clear()

This method clears the `Ref` object.

#### Syntax

    void clear();

### 13.25.3 getConnection()

Returns the connection from which the `Ref` object was instantiated.

#### Syntax

    const Connection *getConnection() const;

### 13.25.4 isClear()

This method checks if `Ref` object is cleared.

#### Syntax

    bool isClear() const;

### 13.25.5 isNull()

This method tests whether the `Ref` object is `NULL`. If the `Ref` object is `NULL`, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool isNull() const;

### 13.25.6 markDelete()

This method marks the referenced object as deleted.

#### Syntax

    void markDelete();

### 13.25.7 operator-\>()

This method dereferences the `Ref` object and pins, or fetches the referenced object if necessary. This might result in prefetching a graph of objects if prefetch attributes of the referenced object are set.

| Syntax                         | Description                                                  |
|:-------------------------------|:-------------------------------------------------------------|
| `T *operator->();`             | Dereferences and pins or fetches a non-`const` `Ref` object. |
| `const T *operator->() const;` | Dereferences and pins or fetches a `const` `Ref` object.     |

### 13.25.8 operator\*()

This method dereferences the `Ref` object and pins or fetches the referenced object if necessary. This might result in prefetching a graph of objects if prefetch attributes of the referenced object are set. The object does not have to be deleted. Destructor would be automatically called when it goes out of scope.

| Syntax                        | Description                                                  |
|:------------------------------|:-------------------------------------------------------------|
| `T& operator*();`             | Dereferences and pins or fetches a non-`const` `Ref` object. |
| `const T& operator*() const;` | Dereferences and pins or fetches a `const` `Ref` object.     |

### 13.25.9 operator==()

This method tests whether two `Ref` objects are referencing the same object. If the `Ref` objects are referencing the same object, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator == (
       const Ref<T> &ref) const;

| Parameter | Description                                  |
|:----------|:---------------------------------------------|
| `ref`     | The Ref object of the object to be compared. |

### 13.25.10 operator!=()

This method tests whether two `Ref` objects are referencing the same object. If the `Ref` objects are not referencing the same object, then `TRUE` is returned; otherwise, `FALSE` is returned.

#### Syntax

    bool operator!= (
       const Ref<T> &ref) const;

| Parameter | Description                                    |
|:----------|:-----------------------------------------------|
| `ref`     | The `Ref` object of the object to be compared. |

### 13.25.11 operator=()

Assigns the `Ref` or the object to a `Ref`. For the first case, the `Ref`s are assigned and for the second case, the `Ref` is constructed from the object and then assigned.

| Syntax                                           | Description                   |
|:-------------------------------------------------|:------------------------------|
| `Ref<T>& operator=(`<br>`   const Ref<T> &src);` | Assigns a `Ref` to a `Ref`.   |
| `Ref<T>& operator=(`<br>`   const T *)obj;`      | Assigns a `Ref` to an object. |

| Parameter | Description                                                     |
|:----------|:----------------------------------------------------------------|
| `src`     | The source `Ref` object to be assigned.                         |
| `obj`     | The source object pointer whose `Ref` object is to be assigned. |

### 13.25.12 ptr()

Returns a pointer to a `PObject`. This operator dereferences the `Ref` and pins or fetches the object if necessary. This might result in prefetching a graph of objects if prefetch attributes of the `Ref` are set.

| Syntax                  | Description                                      |
|:------------------------|:-------------------------------------------------|
| `T *ptr();`             | Returns a pointer of a non-`const` `Ref` object. |
| `const T *ptr() const;` | Returns a pointer of a `const` `Ref` object.     |

### 13.25.13 setLock()

This method specifies how the object should be locked when dereferenced.

#### Syntax

    void setLock(lockOptions);

| Argument      | Description                                                   |
|:--------------|:--------------------------------------------------------------|
| `lockOptions` | The lock options as defined by `LockOptions` in Table 13-35 . |

### 13.25.14 setNull()

This method sets the `Ref` object to `NULL`.

#### Syntax

    void setNull();

### 13.25.15 setPrefetch()

Sets the prefetching options for complex object retrieval. This method specifies depth up to which all objects reachable from this object through `Ref`s (transitive closure) should be prefetched. If only selected attribute types are to be prefetched, then the first version of the method must be used. This method specifies which Ref attributes of the object it refers to should be followed for prefetching of the objects (complex object retrieval) and how many levels deep those links should be followed.

| Syntax                                                                                                            | Description                                                                                                           |
|:------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| `void setPrefetch(`<br>`   const string &typeName,`<br>`   unsigned int depth);`                                  | Sets the prefetching options for complex object retrieval, using type name and depth.                                 |
| `void setPrefetch(`<br>`   unsigned int depth);`                                                                  | Sets the prefetching options for complex object retrieval, using depth only.                                          |
| `void setPrefetch(`<br>`   const string &schName,`<br>`   const string &typeName,`<br>`   unsigned int depth);`   | Sets the prefetching options for complex object retrieval, using schema, type name, and depth.                        |
| `void setPrefetch(`<br>`   const UString &schName,`<br>`   const UString &typeName,`<br>`   unsigned int depth);` | Sets the prefetching options for complex object retrieval, using schema, type name, and depth, and `UString` support. |

| Parameter  | Description                                                                                             |
|:-----------|:--------------------------------------------------------------------------------------------------------|
| `typeName` | Type of the Ref attribute to be prefetched.                                                             |
| `schName`  | Schema name of the Ref attribute to be prefetched.                                                      |
| `depth`    | Depth level to which the links should be followed; can use `PrefetchOption` as defined in Table 13-35 . |

### 13.25.16 unmarkDelete()

This method unmarks the referred object as dirty and available for deletion.

#### Syntax

    void unmarkDelete();
