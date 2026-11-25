The `RefAny` class is designed to support a reference to any type. Its primary purpose is to handle generic references and allow conversions of `Ref` in the type hierarchy. A `RefAny` object can be used as an intermediary between any two types, `Ref<``x``>` and `Ref<``y``>`, where `x` and `y` are different types.

Table 13-37 Summary of RefAny Methods

| Method          | Summary                                                     |
|:----------------|:------------------------------------------------------------|
| RefAny()        | Constructor for `RefAny` class.                             |
| clear()         | Clears the reference.                                       |
| getConnection() | Returns the connection this ref was created from.           |
| isNull()        | Checks if the `RefAny` object is `NULL`.                    |
| markDelete()    | Marks the object as deleted.                                |
| operator=()     | Assignment operator for `RefAny`.                           |
| operator==()    | Checks if this `RefAny` object equals a specified `RefAny`. |
| operator!=()    | Checks if not equal.                                        |
| unmarkDelete()  | Unmarks the object as deleted.                              |

### 13.26.1 RefAny()

A `Ref<T>` can always be converted to a `RefAny`; there is a method to perform the conversion in the `Ref<T>` template. Each `Ref<T>` has a constructor and assignment operator that takes a reference to `RefAny`.

| Syntax                                                                   | Description                                                |
|:-------------------------------------------------------------------------|:-----------------------------------------------------------|
| `RefAny();`                                                              | Creates a `NULL RefAny`.                                   |
| `RefAny(`<br>`   const Connection *sessptr,`<br>`   const OCIRef *ref);` | Creates a `RefAny` from a session pointer and a reference. |
| `RefAny(`<br>`   const RefAny& src);`                                    | Creates a `RefAny` as a copy of another `RefAny` object.   |

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `sessptr` | Session pointer                           |
| `ref`     | A reference                               |
| `src`     | The source `RefAny` object to be assigned |

### 13.26.2 clear()

This method clears the reference.

#### Syntax

    void clear();

### 13.26.3 getConnection()

Returns the connection from which this reference was instantiated.

#### Syntax

    const Connection* getConnection() const;

### 13.26.4 isNull()

Returns `TRUE` if the object pointed to by this ref is `NULL` else `FALSE`.

#### Syntax

    bool isNull() const;

### 13.26.5 markDelete()

This method marks the referred object as deleted.

#### Syntax

    void markDelete();

### 13.26.6 operator=()

Assignment operator for `RefAny`.

#### Syntax

    RefAny& operator=(
       const RefAny& src);

| Parameter | Description                              |
|:----------|:-----------------------------------------|
| `src`     | The source RefAny object to be assigned. |

### 13.26.7 operator==()

Compares this `ref` with a `RefAny` object and returns `TRUE` if both the refs are referring to the same object in the cache, otherwise it returns `FALSE`.

#### Syntax

    bool operator== (
       const RefAny &refAnyR) const;

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `refAnyR` | `RefAny` object to which the comparison is made. |

### 13.26.8 operator!=()

Compares this ref with the RefAny object and returns `TRUE` if both the refs are not referring to the same object in the cache, otherwise it returns `FALSE`.

#### Syntax

    bool operator!= (
       const RefAny &refAnyR) const;

| Parameter | Description                                      |
|:----------|:-------------------------------------------------|
| `refAnyR` | `RefAny` object to which the comparison is made. |

### 13.26.9 unmarkDelete()

This method unmarks the referred object as dirty.

#### Syntax

    void unmarkDelete();
