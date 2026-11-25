Lists and describes the OCI collection and iterator functions.

Table 28-2 describes the OCI collection and iterator functions that are described in this section.

Table 28-2 Collection and Iterator Functions  

| Function              | Purpose                                                               |
|:----------------------|:----------------------------------------------------------------------|
| OCICollAppend()       | Append an element to the end of a collection                          |
| OCICollAssign()       | Assign (deep copy) one collection to another                          |
| OCICollAssignElem()   | Assign the given element value `elem` to the element at `coll[index]` |
| OCICollGetElem()      | Get pointer to an element                                             |
| OCICollGetElemArray() | Get an array of elements from a collection                            |
| OCICollIsLocator()    | Indicate whether a collection is locator-based or not                 |
| OCICollMax()          | Return maximum number of elements in collection                       |
| OCICollSize()         | Get current size of collection (in number of elements)                |
| OCICollTrim()         | Trim elements from the collection                                     |
| OCIIterCreate()       | Create iterator to scan the varray elements                           |
| OCIIterDelete()       | Delete iterator                                                       |
| OCIIterGetCurrent()   | Get current collection element                                        |
| OCIIterInit()         | Initialize iterator to scan the given collection                      |
| OCIIterNext()         | Get next collection element                                           |
| OCIIterPrev()         | Get previous collection element                                       |

### 28.2.1 OCICollAppend()

Appends an element to the end of a collection.

#### Purpose

Appends an element to the end of a collection.

#### Syntax

    sword OCICollAppend ( OCIEnv              *env,
                          OCIError            *err,
                          const void          *elem,
                          const void          *elemind,
                          OCIColl             *coll );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

elem (IN)
Pointer to the element to be appended to the end of the given collection.

elemind (IN) \[optional\]
Pointer to the element's `NULL` indicator information. If (`elemind` == NULL) then the `NULL` indicator information of the appended element is set to non-`NULL`.

coll (IN/OUT)
Updated collection.

#### Comments

Appending an element is equivalent to increasing the size of the collection by one element and updating (deep copying) the last element's data with the given element's data. Note that the pointer to the given element `elem` is not saved by this function, which means that `elem` is strictly an input parameter.

`OCICollAppend()` creates an element at index 0 if no elements exist. The method (array bind) for binding PL/SQL index-by tables assumes a start index of 1.

#### Returns

This function returns an error if the current size of the collection equals the maximum size (upper bound) of the collection before appending the element. This function also returns an error if any of the input parameters is `NULL`.

**Related Topics**

- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.2 OCICollAssign()

Assigns (deep copies) one collection to another.

#### Purpose

Assigns (deep copies) one collection to another.

#### Syntax

    sword OCICollAssign ( OCIEnv              *env,
                          OCIError            *err,
                          const OCIColl       *rhs,
                          OCIColl             *lhs );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

rhs (IN)
Right-hand side (source) collection to be assigned from.

lhs (OUT)
Left-hand side (target) collection to be assigned to.

#### Comments

Assigns `rhs` (source) to `lhs` (target). The `lhs` collection may be decreased or increased depending upon the size of `rhs`. If the `lhs` collection contains any elements, then the elements are deleted before the assignment. This function performs a deep copy. The memory for the elements comes from the object cache.

#### Returns

An error is returned if the element types of the `lhs` and `rhs` collections do not match. Also, an error is returned if the upper bound of the `lhs` collection is less than the current number of elements in the `rhs` collection. An error is also returned if:

- Any of the input parameters is `NULL`

- There is a type mismatch between the `lhs` and `rhs` collections

- The upper bound of the `lhs` collection is less than the current number of elements in the `rhs` collection

**Related Topics**

- OCICollAssignElem()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.3 OCICollAssignElem()

Assigns the given element value `elem` to the element at `coll[index]`.

#### Purpose

Assigns the given element value `elem` to the element at `coll[index]`.

#### Syntax

    sword OCICollAssignElem ( OCIEnv           *env,
                              OCIError         *err,
                              sb4               index,
                              const void       *elem,
                              const void       *elemind,
                              OCIColl          *coll );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

index (IN)
Index of the element to which the element is assigned.

elem (IN)
Source element from which the element is assigned. See [Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `elem`.

elemind (IN) \[optional\]
Pointer to the element's `NULL` indicator information; if (`elemind` == `NULL`), then the `NULL` indicator information of the assigned element is set to non-`NULL`.

coll (IN/OUT)
Collection to be updated.

#### Comments

If the collection is of type nested table, the element at the given index might not exist, as when an element has been deleted. In this case, the given element is inserted at `index`. Otherwise, the element at `index` is updated with the value of `elem`.

Note that the given element is deep copied, and `elem` is strictly an input parameter.

#### Returns

This function returns an error if any input parameter is `NULL` or if the given index is beyond the bounds of the given collection.

**Related Topics**

- OCICollAssign()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.4 OCICollGetElem()

Gets a pointer to the element at the given index.

#### Purpose

Gets a pointer to the element at the given index.

#### Syntax

    sword OCICollGetElem ( OCIEnv           *env,
                           OCIError         *err,
                           const OCIColl    *coll,
                           sb4               index,
                           boolean          *exists,
                           void            **elem,
                           void            **elemind );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
Pointer to the element in this collection to be returned.

index (IN)
Index of the element whose pointer is returned.

exists (OUT)
Set to `FALSE` if the element at the specified index does not exist; otherwise, set to `TRUE`.

elem (OUT)
Address of the element to be returned.

elemind (OUT) \[optional\]
Address of the `NULL` indicator information is returned. If (`elemind` == `NULL`), then the `NULL` indicator information is not returned.

#### Comments

Gets the address of the element at the given position. Optionally, this function also returns the address of the element's `NULL` indicator information.

Table 28-3 describes for each OCI type code value, the element pointer type, and what the corresponding collection element type is. The element pointer is returned with the `elem` parameter of `OCICollGetElem()`. See the table for object data type mappings for object type attributes in [About Mapping Object Data Types to C](using-object-type-translator-in-oci.md)for a more complete list of the `OCITypeCode` values.

Table 28-3 Element Pointers

| OCITypeCode Values                                       | \*elem Is Set to  | Element Type                          |
|:---------------------------------------------------------|:------------------|:--------------------------------------|
| OCI_TYPECODE_NUMBER                                      | `OCINumber*`      | Oracle `NUMBER` (`OCINumber`)         |
| OCI_TYPECODE_DATE                                        | `OCIDate*`        | Date (`OCIDate`)                      |
| OCI_TYPECODE_TIMESTAMP                                   | `OCIDateTime*`    | Datetime (`OCIDateTime`)              |
| OCI_TYPECODE_INTERVAL_YM, OCI_TYPECODE_INTERVAL_DS       | `OCIInterval*`    | Interval (`OCIInterval`)              |
| OCI_TYPECODE_CHAR (n), OCI_TYPECODE_NCHAR                | `OCIString**`     | Variable-length string (`OCIString*`) |
| OCI_TYPECODE_RAW                                         | `OCIRaw**`        | Variable-length raw (`OCIRaw*`)       |
| OCI_TYPECODE_REF                                         | `OCIRef**`        | Object reference (`OCIRef*`)          |
| OCI_TYPECODE_BLOB, OCI_TYPECODE_CLOB, OCI_TYPECODE_NCLOB | `OCILobLocator**` | Lob locator (`OCILobLocator*`)        |
| OCI_TYPECODE_OBJECT                                      | `person*`         | Object type (such as person)          |
| OCI_TYPECODE_NAMEDCOLLECTION                             | `OCIColl *`       | Collections                           |

The element pointer returned by `OCICollGetElem()` is in a form that can be used not only to access the element data but also to serve as the target (left-hand side) of an assignment statement.

For example, assume the user is iterating over the elements of a collection whose element type is object reference (`OCIRef*`). A call to `OCICollGetElem()` returns the pointer to a reference handle (`OCIRef**`). After getting the pointer to the collection element, you may want to modify it by assigning a new reference.

The following code example shows how this can be accomplished with the `OCIRefAssign()` function.

Assigning a New Reference to the Pointer to the Collection Element

    sword OCIRefAssign( OCIEnv       *env,
                        OCIError     *err,
                        const OCIRef *source,
                        OCIRef       **target );

Note that the `target` parameter of `OCIRefAssign()` is of type `OCIRef**`. Hence `OCICollGetElem()` returns `OCIRef**`. If `*target` equals `NULL`, a new `REF` is allocated by `OCIRefAssign()` and returned in the `target` parameter.

Similarly, if the collection element was of type string (`OCIString*`), `OCICollGetElem()` returns the pointer to the string handle (that is, `OCIString**`). If a new string is assigned, through `OCIStringAssign()` or `OCIStringAssignText()`, the type of the target must be `OCIString **`.

If the collection element is of type Oracle `NUMBER`, `OCICollGetElem()` returns `OCINumber*`. The following code example shows the prototype of the `OCINumberAssign()` call.

Prototype of OCINumberAssign() Call

    sword OCINumberAssign(OCIError        *err,
                          const OCINumber *from,
                          OCINumber       *to);

#### Returns

The `OCICollGetElem()` function returns an error if any of the input parameters is `NULL`.

**Related Topics**

- OCICollAssignElem()
- [OCIRefAssign()](oci-REF-functions.md)
- [OCIStringAssign()](oci-string-functions.md)
- [OCIStringAssignText()](oci-string-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.5 OCICollGetElemArray()

Gets an array of elements from a collection when given a starting index.

#### Purpose

Gets an array of elements from a collection when given a starting index.

#### Syntax

    sword OCICollGetElemArray ( OCIEnv              *env,
                                OCIError            *err,
                                const OCIColl       *coll,
                                sb4                  index,
                                boolean             *exists,
                                void               **elem,
                                void               **elemind,
                                uword               *nelems );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
Pointers to the elements in this collection to be returned.

index (IN)
Starting index of the elements.

exists (OUT)
Is set to `FALSE` if the element at the specified index does not exist; otherwise, it is set to `TRUE`.

elem (OUT)
Address of the desired elements to be returned.

elemind (OUT) \[optional\]
Address of the `NULL` indicator information to be returned. If (`elemind == NULL`), then the `NULL` indicator information is not returned.

nelems (IN)
Maximum number of pointers to both `elem` and `elemind`.

#### Comments

Gets the address of the elements from the given position.

For index by integer collections, `OCICollGetElemArray()` gets the elements beginning at the given index, but loses the index information for each element in the process. Users are able to get the element data beginning at that index as an array, but cannot get the index for each element in the array. This behavior is similar to what happens for the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions.

#### Returns

Optionally, this function also returns the address of the element's `NULL` indicator information.

**Related Topics**

- OCICollGetElem()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterCreate()
- OCIIterDelete()
- OCIIterGetCurrent()
- OCIIterInit()
- OCIIterNext()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.6 OCICollIsLocator()

Indicates whether a collection is locator-based or not.

#### Purpose

Indicates whether a collection is locator-based or not.

#### Syntax

    sword OCICollIsLocator ( OCIEnv           *env,
                             OCIError         *err,
                             const OCIColl    *coll,
                             boolean          *result );

#### Parameters

env (IN)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
A collection item.

result (OUT)
Returns `TRUE` if the collection item is locator-based, `FALSE` otherwise.

#### Comments

This function tests to see whether a collection is locator-based.

#### Returns

Returns `TRUE` in the `result` parameter if the collection item is locator-based; otherwise, it returns `FALSE`.

**Related Topics**

- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.7 OCICollMax()

Gets the maximum size in number of elements of the given collection.

#### Purpose

Gets the maximum size in number of elements of the given collection.

#### Syntax

    sb4 OCICollMax ( OCIEnv           *env,
                     const OCIColl    *coll );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

coll (IN)
Collection whose number of elements is returned. The `coll` parameter must point to a valid collection descriptor.

#### Comments

Returns the maximum number of elements that the given collection can hold. A value of zero indicates that the collection has no upper bound.

For collections that do not support negative indexes, the largest index number is also the maximum size of the collection. However, this is not true for index-by integer collections because some of the elements can have negative indexes, so the largest index numbered element is not the same as the maximum collection size.

#### Returns

The upper bound of the given collection.

The return value is always 0 (no upper bound) for index-by integer collections.

**Related Topics**

- OCICollSize()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.8 OCICollSize()

Gets the current size in number of elements of the given collection.

#### Purpose

Gets the current size in number of elements of the given collection.

#### Syntax

    sword OCICollSize ( OCIEnv           *env,
                        OCIError         *err,
                        const OCIColl    *coll
                        sb4              *size );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
Collection whose number of elements is returned. Must point to a valid collection descriptor.

size (OUT)
Current number of elements in the collection.

#### Comments

Returns the current number of elements in the given collection. For a nested table, this count is not decremented when elements are deleted. So, this count includes any holes created by deleting elements. A trim operation (`OCICollTrim()`) decrements the count by the number of trimmed elements. To get the count minus the deleted elements use `OCITableSize()`.

The following pseudocode shows some examples:

    OCICollSize(...);
    // assume 'size' returned is equal to 5
    OCITableDelete(...); // delete one element
    OCICollSize(...);
    // 'size' returned is still 5

To get the count minus the deleted elements use `OCITableSize()`. Continuing the earlier example:

    OCITableSize(...)
    // 'size' returned is equal to 4

A trim operation `OCICollTrim()`) decrements the count by the number of trimmed elements. Continuing the earlier example:

    OCICollTrim(..,1..); // trim one element
    OCICollSize(...);
    // 'size' returned is equal to 4

#### Returns

The `OCICollSize()` function returns an error if an error occurs during the loading of the collection into the object cache or if any of the input parameters is `NULL`.

**Related Topics**

- OCICollMax()
- OCICollTrim()
- [OCITableSize()](oci-table-functions.md)
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.9 OCICollTrim()

Trims the given number of elements from the end of the collection.

#### Purpose

Trims the given number of elements from the end of the collection.

#### Syntax

    sword OCICollTrim ( OCIEnv         *env,
                        OCIError       *err,
                        sb4             trim_num,
                        OCIColl        *coll );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

trim_num (IN)
Number of elements to trim.

coll (IN/OUT)
Removes (frees) `trim_num` of elements from the end of the collection `coll`.

#### Comments

The elements are removed from the end of the collection.

#### Returns

An error is returned if `trim_num` is greater than the current size of the collection.

**Related Topics**

- OCICollSize()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.10 OCIIterCreate()

Creates an iterator to scan the elements or the collection.

#### Purpose

Creates an iterator to scan the elements or the collection.

#### Syntax

    sword OCIIterCreate ( OCIEnv               *env,
                          OCIError             *err,
                          const OCIColl        *coll,
                          OCIIter             **itr );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
Collection that is scanned. For Oracle8i or later, valid collection types include varrays and nested tables.

itr (OUT)
Address to the allocated collection iterator to be returned by this function.

#### Comments

The iterator is created in the object cache. The iterator is initialized to point to the beginning of the collection.

If `OCIIterNext()` is called immediately after creating the iterator, then the first element of the collection is returned. If `OCIIterPrev()` is called immediately after creating the iterator, then an "at beginning of collection" error is returned.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

This function returns an error if any of the input parameters is `NULL`.

**Related Topics**

- OCIIterDelete()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterGetCurrent()
- OCIIterInit()
- OCIIterNext()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.11 OCIIterDelete()

Deletes a collection iterator.

#### Purpose

Deletes a collection iterator.

#### Syntax

    sword OCIIterDelete ( OCIEnv           *env,
                          OCIError         *err,
                          OCIIter         **itr );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

itr (IN/OUT)
The allocated collection iterator that is destroyed and set to `NULL` before returning.

#### Comments

Deletes an iterator that was previously created by a call to `OCIIterCreate()`.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

This function returns an error if any of the input parameters is `NULL`.

**Related Topics**

- OCIIterCreate()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterGetCurrent()
- OCIIterInit()
- OCIIterNext()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.12 OCIIterGetCurrent()

Gets a pointer to the current iterator collection element.

#### Purpose

Gets a pointer to the current iterator collection element.

#### Syntax

    sword OCIIterGetCurrent ( OCIEnv             *env,
                              OCIError           *err,
                              const OCIIter      *itr,
                              void              **elem,
                              void              **elemind );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

itr (IN)
Iterator that points to the current element.

elem (OUT)
Address of the element pointed to by the iterator to be returned. See [Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `elem`.

elemind (OUT) \[optional\]
Address of the element's `NULL` indicator information to be returned; if (`elem_ind` == NULL) then the `NULL` indicator information is not returned.

#### Comments

Returns the pointer to the current iterator collection element and its corresponding `NULL` information.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

This function returns an error if any input parameter is `NULL`.

**Related Topics**

- OCIIterCreate()
- OCIIterDelete()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterInit()
- OCIIterNext()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.13 OCIIterInit()

Initializes an iterator to scan a collection.

#### Purpose

Initializes an iterator to scan a collection.

#### Syntax

    sword OCIIterInit ( OCIEnv              *env,
                        OCIError            *err,
                        const OCIColl       *coll,
                        OCIIter             *itr );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

coll (IN)
Collection that is scanned. For Oracle8i or later, valid collection types include varrays and nested tables.

itr (IN/OUT)
Pointer to an allocated collection iterator.

#### Comments

Initializes at the given iterator to point to the beginning of the given collection. You can use this function to perform either of the following tasks:

- Reset an iterator to point back to the beginning of the collection.

- Reuse an allocated iterator to scan a different collection.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

Returns an error if any input parameter is `NULL`.

**Related Topics**

- OCIIterCreate()
- OCIIterDelete()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterGetCurrent()
- OCIIterNext()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.14 OCIIterNext()

Gets a pointer to the next iterator collection element.

#### Purpose

Gets a pointer to the next iterator collection element.

#### Syntax

    sword OCIIterNext ( OCIEnv            *env,
                        OCIError          *err,
                        OCIIter           *itr,
                        void             **elem,
                        void             **elemind,
                        boolean           *eoc);

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`..

itr (IN/OUT)
Iterator that is updated to point to the next element.

elem (OUT)
Address of the next element; returned after the iterator is updated to point to it. See [Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `elem`.

elemind (OUT) \[optional\]
Address of the element's `NULL` indicator information; if (`elem_ind` == `NULL`), then the `NULL` indicator information is not returned.

eoc (OUT)
`TRUE` if the iterator is at the end of the collection (that is, the next element does not exist); otherwise, `FALSE`.

#### Comments

This function returns a pointer to the next iterator collection element and its corresponding `NULL` information. It also updates the iterator to point to the next element.

If the iterator is pointing to the last element of the collection before you execute this function, then calling this function sets the `eoc` flag to `TRUE`. The iterator is left unchanged in that case.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

This function returns an error if any input parameter is `NULL`.

**Related Topics**

- OCIIterCreate()
- OCIIterDelete()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterGetCurrent()
- OCIIterInit()
- OCIIterPrev()
- [OCIErrorGet()](miscellaneous-functions.md)

### 28.2.15 OCIIterPrev()

Gets a pointer to the previous iterator collection element.

#### Purpose

Gets a pointer to the previous iterator collection element.

#### Syntax

    sword OCIIterPrev ( OCIEnv            *env,
                        OCIError          *err,
                        OCIIter           *itr,
                        void             **elem,
                        void             **elemind,
                        boolean           *boc );

#### Parameters

env (IN/OUT)
The OCI environment handle initialized in object mode. See the descriptions of `OCIEnvCreate()`, `OCIEnvNlsCreate()`, and `OCIInitialize()` (deprecated) for more information.

err (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

itr (IN/OUT)
Iterator that is updated to point to the previous element.

elem (OUT)
Address of the previous element; returned after the iterator is updated to point to it. See [Table 24-1](using-object-type-translator-in-oci.md) that lists the type of data and what C data type can be found in parameter `elem`.

elemind (OUT) \[optional\]
Address of the element's `NULL` indicator information; if (`elemind` == `NULL`), then the `NULL` indicator information is not returned.

boc (OUT)
`TRUE` if iterator is at the beginning of the collection (that is, the previous element does not exist); otherwise, `FALSE`.

#### Comments

This function returns a pointer to the previous iterator collection element and its corresponding `NULL` information. The iterator is updated to point to the previous element.

If the iterator is pointing to the first element of the collection before you execute this function, then calling this function sets `boc` to `TRUE`. The iterator is left unchanged in that case.

For index-by integer collections, the `OCIIterCreate()`, `OCIIterDelete()`, `OCIIterGetCurrent()`, `OCIIterInit()`, `OCIIterNext()`, and `OCIIterPrev()` functions all ignore the index for each element in the collection. That is, `OCIIterGetCurrent()` returns only the element value and not the index of the element.

#### Returns

This function returns an error if any input parameter is `NULL`.

**Related Topics**

- OCIIterCreate()
- OCIIterDelete()
- [OCIEnvCreate()](connect-authorize-and-initialize-functions.md)
- [OCIEnvNlsCreate()](connect-authorize-and-initialize-functions.md)
- [OCIInitialize()](deprecated-oci-functions.md)
- OCIIterGetCurrent()
- OCIIterInit()
- OCIIterNext()
- [OCIErrorGet()](miscellaneous-functions.md)
