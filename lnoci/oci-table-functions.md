Lists and describes the OCI table functions.

Table 28-17 describes the OCI table functions that are described in this section.

Table 28-17 Table Functions

| Function         | Purpose                                  |
|:-----------------|:-----------------------------------------|
| OCITableDelete() | Delete element                           |
| OCITableExists() | Test whether element exists              |
| OCITableFirst()  | Return first index of table              |
| OCITableLast()   | Return last index of table               |
| OCITableNext()   | Return next available index of table     |
| OCITablePrev()   | Return previous available index of table |
| OCITableSize()   | Return current size of table             |

### 28.8.1 OCITableDelete()

Deletes the element at the specified index.

#### Purpose

Deletes the element at the specified index.

#### Syntax

    sword OCITableDelete ( OCIEnv          *env,
                           OCIError        *err,
                           sb4              index,
                           OCITable        *tbl );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

index (IN)
Index of the element that must be deleted.

tbl (IN)
Table whose element is deleted.

#### Comments

This function returns an error if the element at the given index has already been deleted or if the given index is not valid for the given table.

**Note:**

The position ordinals of the remaining elements of the table are not changed by `OCITableDelete()`. The delete operation creates holes in the table.

#### Returns

An error is also returned if any input parameter is `NULL`.

**Related Topics**

- OCITableExists()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.8.2 OCITableExists()

Tests whether an element exists at the given index.

#### Purpose

Tests whether an element exists at the given index.

#### Syntax

    sword OCITableExists ( OCIEnv              *env,
                           OCIError            *err,
                           const OCITable      *tbl,
                           sb4                 index,
                           boolean             *exists );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tbl (IN)
Table in which the given index is checked.

index (IN)
Index of the element that is checked for existence.

exists (OUT)
Set to `TRUE` if the element at the given `index` exists; otherwise, it is set to `FALSE`.

#### Returns

This function returns an error if any input parameter is `NULL`.

**Related Topics**

- OCITableDelete()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.8.3 OCITableFirst()

Returns the index of the first existing element in a given table.

#### Purpose

Returns the index of the first existing element in a given table.

#### Syntax

    sword OCITableFirst ( OCIEnv             *env,
                          OCIError           *err,
                          const OCITable     *tbl,
                          sb4                *index  );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tbl (IN)
Table to scan.

index (OUT)
First index of the element that exists in the given table that is returned.

#### Comments

If `OCITableDelete()` deletes the first five elements of a table, `OCITableFirst()` returns the value 6.

**See Also:**

OCITableDelete() for information regarding non-data holes (deleted elements) in tables

#### Returns

This function returns an error if the table is empty.

**Related Topics**

- OCITableDelete()
- OCITableLast()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.8.4 OCITableLast()

Returns the index of the last existing element of a table.

#### Purpose

Returns the index of the last existing element of a table.

#### Syntax

    sword OCITableLast ( OCIEnv              *env,
                         OCIError            *err,
                         const OCITable      *tbl,
                         sb4                 *index );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tbl (IN)
Table to scan.

index (OUT)
Index of the last existing element in the table.

#### Comments

`OCITableLast()` returns the largest index numbered element in the index by integer collection.

#### Returns

This function returns an error if the table is empty.

**Related Topics**

- OCITableFirst()
- OCITableNext()
- OCITablePrev()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.8.5 OCITableNext()

Returns the index of the next existing element of a table.

#### Purpose

Returns the index of the next existing element of a table.

#### Syntax

    sword OCITableNext ( OCIEnv             *env,
                         OCIError           *err,
                         sb4                 index,
                         const OCITable     *tbl,
                         sb4                *next_index
                         boolean            *exists );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

index (IN)
Index for the starting point of the scan.

tbl (IN)
Table to scan.

next_index (OUT)
Index of the next existing element after `tbl`(`index`).

exists (OUT)
`FALSE` if no next index is available; otherwise, `TRUE`.

#### Returns

Returns the smallest position `j`, greater than `index`, such that `exists(j)` is `TRUE`.

**Related Topics**

- OCITablePrev()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

The description of OCITableSize() for information about the existence of non-data holes (deleted elements) in tables

### 28.8.6 OCITablePrev()

Returns the index of the previous existing element of a table.

#### Purpose

Returns the index of the previous existing element of a table.

#### Syntax

    sword OCITablePrev ( OCIEnv             *env,
                         OCIError           *err,
                         sb4                 index,
                         const OCITable     *tbl,
                         sb4                *prev_index
                         boolean            *exists );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

index (IN)
Index for the starting point of the scan.

tbl (IN)
Table to scan.

prev_index (OUT)
Index of the previous existing element before `tbl`(`index`).

exists (OUT)
`FALSE` if no previous index is available; otherwise, `TRUE`.

#### Returns

Returns the largest position `j`, less than `index`, such that `exists (j)` is `TRUE`.

**Related Topics**

- OCITableNext()
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

**See Also:**

The description of OCITableSize() for information about the existence of non-data holes (deleted elements) in tables

### 28.8.7 OCITableSize()

Returns the size of the given table, not including any holes created by deleted elements.

#### Purpose

Returns the size of the given table, not including any holes created by deleted elements.

#### Syntax

    sword OCITableSize ( OCIEnv             *env,
                         OCIError           *err,
                         const OCITable     *tbl
                         sb4                *size );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tbl (IN)
Nested table whose number of elements is returned.

size (OUT)
Current number of elements in the nested table. The count does not include deleted elements.

#### Comments

The count is decremented when elements are deleted from the nested table. So this count does not include any holes created by deleting elements. To get the count including the holes created by the deleted elements, use `OCICollSize()`.

The following code example shows a code fragment where an element is deleted from a nested table.

Deleting an Element from a Nested table

    OCITableSize(...);
    // assume 'size' returned is equal to 5
    OCITableDelete(...); // delete one element
    OCITableSize(...);
    // 'size' returned is equal to 4

To get the count plus the count of deleted elements, use `OCICollSize()`, as shown in the following code example. Continuing the previous code example.

Getting a Count of All Elements Including Deleted Elements from a Nested Table

    OCICollSize(...)
    // 'size' returned is still equal to 5

#### Returns

This function returns an error if an error occurs during the loading of the nested table into the object cache, or if any of the input parameters is `NULL`.

**Related Topics**

- [OCICollSize()](oci-collection-and-iterator-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
