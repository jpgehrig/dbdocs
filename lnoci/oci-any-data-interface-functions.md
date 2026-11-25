Lists and describes OCI Any Data interface functions.

Table 30-3 lists the Any Data Interface functions that are described in this section.

Table 30-3 Any Data Functions  

| Function                   | Purpose                                                                                                                                               |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| OCIAnyDataAccess()         | Retrieve the data value of an `OCIAnyData`                                                                                                            |
| OCIAnyDataAttrGet()        | Get the value of the attribute at the current position in the `OCIAnyData`                                                                            |
| OCIAnyDataAttrSet()        | Set the attribute at the current position with a given value                                                                                          |
| OCIAnyDataBeginCreate()    | Allocate an `OCIAnyData` for the given duration and initialize it with the type information                                                           |
| OCIAnyDataCollAddElem()    | Add the next collection element to the collection attribute of the `OCIAnyData` at the current attribute position                                     |
| OCIAnyDataCollGetElem()    | Access sequentially the elements in the collection attribute at the current position in the `OCIAnyData`                                              |
| OCIAnyDataConvert()        | Construct an `OCIAnyData` with the given data value of the given type                                                                                 |
| OCIAnyDataDestroy()        | Free an AnyData                                                                                                                                       |
| OCIAnyDataEndCreate()      | Mark the end of `OCIAnyData` creation                                                                                                                 |
| OCIAnyDataGetCurrAttrNum() | Return the current attribute number of the `OCIAnyData`                                                                                               |
| OCIAnyDataGetType()        | Get the type corresponding to an AnyData value                                                                                                        |
| OCIAnyDataIsNull()         | Check if `OCIAnyData` is `NULL`                                                                                                                       |
| OCIAnyDataTypeCodeToSqlt() | Convert the `OCITypeCode` for an AnyData value to the SQLT code that corresponds to the representation of the value as returned by the OCIAnyData API |

### 30.3.1 OCIAnyDataAccess()

Retrieve the data value of an `OCIAnyData`.

#### Purpose

The data value should be of the type with which the `OCIAnyData` was initialized. You can use this call to access an entire `OCIAnyData`, which can be of type `OCI_TYPECODE_OBJECT`, any of the collection types, or any of the built-in types.

#### Syntax

    sword OCIAnyDataAccess ( OCISvcCtx    *svchp,
                             OCIError     *errhp,
                             OCIAnyData   *sdata,
                             OCITypeCode   tc,
                             OCIType      *inst_type,
                             void         *null_ind,
                             void         *data_value,
                             ub4          *length );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN)
Initialized pointer to an `OCIAnyData`.

tc (IN)
Typecode of the data value. This is used for type checking (with the initialization type of the `OCIAnyData`).

inst_type (IN)
The `OCIType` of the data value (if it is not a primitive one). If the `tc` parameter is any of the following types, then this parameter should be not `NULL`.

- `OCI_TYPECODE_OBJECT`

- `OCI_TYPECODE_REF`

- `OCI_TYPECODE_VARRAY`

- `OCI_TYPECODE_TABLE`

Otherwise, it could be `NULL`.

null_ind (OUT)
Indicates if the `data_value` is `NULL`. Pass an `(OCIInd *)` for all typecodes except `OCI_TYPECODE_OBJECT`. The value returned is `OCI_IND_NOTNULL` if the value is not `NULL`, and it is `OCI_IND_NULL` for a `NULL` value. If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer to the indicator struct of the `data_value` as the argument here. See `OCIAnyDataAttrGet()` for details.

data_value (OUT)
The data value (is of the type with which the `OCIAnyData` was initialized). See `OCIAnyDataAttrGet()` for the appropriate C type corresponding to each allowed typecode and for a description of how memory allocation behavior depends on the value passed for this parameter.

length (OUT)
Currently, this parameter is ignored. In the future, this may be used for certain typecodes where the data representation itself does not give the length, in bytes, implicitly.

**Related Topics**

- OCIAnyDataAttrGet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.2 OCIAnyDataAttrGet()

Gets the value of the attribute at the current position in the `OCIAnyData`.

#### Purpose

Attribute values can be accessed sequentially.

#### Syntax

    sword OCIAnyDataAttrGet ( OCISvcCtx    *svchp,
                              OCIError     *errhp,
                              OCIAnyData   *sdata,
                              OCITypeCode   tc,
                              OCIType      *attr_type,
                              void         *null_ind,
                              void         *attr_value,
                              ub4          *length,
                              boolean       is_any );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN/OUT)
Pointer to initialized type `OCIAnyData`.

tc (IN)
Typecode of the attribute. Type checking happens based on `tc`, `attr_type`, and the type information in the `OCIAnyData`.

attr_type (IN) \[optional\]
The `attr_type` parameter should give the type description of the referenced type (for `OCI_TYPECODE_REF`) or the type description of the collection type (for `OCI_TYPECODE_VARRAY`, `OCI_TYPECODE_TABLE`), or the type description of the object (for `OCI_TYPECODE_OBJECT`). This parameter is not required for built-in typecodes.

null_ind (OUT)
Indicates if the `attr_value` is `NULL`. Pass `(OCIInd *)` in `null_ind` for all typecodes except `OCI_TYPECODE_OBJECT`.

If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer `(void **) `in `null_ind`.

The indicator returned is `OCI_IND_NOTNULL` if the value is not `NULL`, and it is `OCI_IND_NULL` for a `NULL` value.

attr_value (IN/OUT)
Value for the attribute.

length (IN/OUT)
Currently, this parameter is ignored. Pass 0 here. In the future, this may be used for certain typecodes where the data representation itself does not give the length, in bytes, implicitly.

is_any (IN)
Is attribute to be returned in the form of `OCIAnyData`?

#### Comments

You can use this call with an `OCIAnyData` of typecode `OCI_TYPECODE_OBJECT` only.

- This call gets the value of the attribute at the current position in the `OCIAnyData`.

- The `tc` parameter must match the type of the attribute at the current position; otherwise, an error is returned.

- The `is_any` parameter is applicable only when the typecode of the attribute is one of these values:

  - `OCI_TYPECODE_OBJECT`

  - `OCI_TYPECODE_VARRAY`

  - `OCI_TYPECODE_TABLE`

  If `is_any` is `TRUE`, then `attr_value` is returned in the form of `OCIAnyData*`.

- You must allocate the memory for the attribute before calling the function. You can allocate memory through `OCIObjectNew()`. For built-in types such as `NUMBER` and `VARCHAR`, the attribute can be just a pointer to a stack variable. Table 30-4 lists the available Oracle data types that can be used as object attribute types and the corresponding types of the attribute value that should be passed.

Table 30-4 Data Types and Attribute Values

| Data Types                          | attr_value                                              |
|:------------------------------------|:--------------------------------------------------------|
| `VARCHAR2, VARCHAR, CHAR `          | `OCIString **`                                          |
| `NUMBER, REAL, INT, FLOAT, DECIMAL` | `OCINumber **`                                          |
| `DATE`                              | `OCIDate **`                                            |
| `TIMESTAMP`                         | `OCIDateTime **`                                        |
| `TIMESTAMP WITH TIME ZONE`          | `OCIDateTime **`                                        |
| `TIMESTAMP WITH LOCAL TIME ZONE`    | `OCIDateTime **`                                        |
| `INTERVAL YEAR TO MONTH`            | `OCIInterval **`                                        |
| `INTERVAL DAY TO SECOND`            | `OCIInterval **`                                        |
| `BLOB`                              | `OCILobLocator **` or `OCIBlobLocator **`               |
| `CLOB`                              | `OCILobLocator **` or `OCIClobLocator *`                |
| `BFILE`                             | `OCILobLocator **`                                      |
| `REF`                               | `OCIRef **`                                             |
| `RAW`                               | `OCIRaw **`                                             |
| `VARRAY`                            | `OCIArray **` (or `OCIAnyData *` if `is_any` is `TRUE`) |
| `TABLE`                             | `OCITable **` (or `OCIAnyData *` if `is_any` is `TRUE`) |
| `OBJECT`                            | `void **` (or `OCIAnyData *` if `is_any` is `TRUE`)     |

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.3 OCIAnyDataAttrSet()

Sets the attribute at the current position with a given value.

#### Purpose

Sets the attribute at the current position with a given value.

#### Syntax

    sword OCIAnyDataAttrSet ( OCISvcCtx    *svchp,
                              OCIError     *errhp,
                              OCIAnyData   *sdata,
                              OCITypeCode   tc,
                              OCIType      *attr_type,
                              void         *null_ind,
                              void         *attr_value,
                              ub4           length,
                              boolean       is_any );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN/OUT)
Initialized `OCIAnyData`.

tc (IN)
Typecode of the attribute. Type checking happens based on `tc`, `attr_type`, and the type information in the `OCIAnyData`.

attr_type (IN) \[optional\]
The `attr_type` parameter gives the type description of the referenced type (for `OCI_TYPECODE_REF`), the type description of the collection type (for `OCI_TYPECODE_VARRAY`, `OCI_TYPECODE_TABLE`), and the type description of the object (for `OCI_TYPECODE_OBJECT`). This parameter is not required for built-in typecodes or if `OCI_TYPECODE_NONE` is specified.

null_ind (IN)
Indicates if the `attr_value` is `NULL`. Pass `(OCIInd *)` for all typecodes except `OCI_TYPECODE_OBJECT`. The indicator should be `OCI_IND_NOTNULL` if the value is not `NULL`, and it should be `OCI_IND_NULL` for a `NULL` value.

If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer to the indicator struct of the `attr_value` as the argument here.

attr_value (IN)
Value for the attribute.

length (IN)
Currently, this parameter is ignored. Pass 0 here. In the future, this may be used for certain typecodes where the data representation itself does not give the length implicitly.

is_any (IN)
Is attribute in the form of `OCIAnyData`?

#### Comments

`OCIAnyDataBeginCreate()` creates an `OCIAnyData` with an empty skeleton instance. To fill the attribute values, use `OCIAnyDataAttrSet()` (for `OCI_TYPECODE_OBJECT`) or `OCIAnyDataCollAddElem()` (for the collection typecodes).

Attribute values must be set in order, from the first attribute to the last. The current attribute number is remembered as the state maintained inside the `OCIAnyData`. Piece-wise construction of embedded attributes and collection elements is not yet supported.

This call sets the attribute at the current position with `attr_value`. Once piece-wise construction has started for an `OCIAnyData` instance, the `OCIAnyDataConstruct()` calls can no longer be used.

The `tc` parameter must match the type of the attribute at the current position. Otherwise, an error is returned.

If `is_any` is `TRUE`, then the attribute must be in the form of `OCIAnyData*`, and it is copied into the enclosing `OCIAnyData` (data) without any conversion.

Table 30-5 lists the available data types that can be used as object attribute types and the corresponding types of the attribute value that should be passed.

Table 30-5 Data Types and Attribute Values

| Data Types                          | attr_value                                             |
|:------------------------------------|:-------------------------------------------------------|
| `VARCHAR2, VARCHAR, CHAR `          | `OCIString *`                                          |
| `NUMBER, REAL, INT, FLOAT, DECIMAL` | `OCINumber *`                                          |
| `DATE`                              | `OCIDate *`                                            |
| `TIMESTAMP`                         | `OCIDateTime *`                                        |
| `TIMESTAMP WITH TIME ZONE`          | `OCIDateTime *`                                        |
| `TIMESTAMP WITH LOCAL TIME ZONE`    | `OCIDateTime *`                                        |
| `INTERVAL YEAR TO MONTH`            | `OCIInterval *`                                        |
| `INTERVAL DAY TO SECOND`            | `OCIInterval *`                                        |
| `BLOB`                              | `OCILobLocator *` or `OCIBlobLocator *`                |
| `CLOB`                              | `OCILobLocator *` or `OCIClobLocator *`                |
| `BFILE`                             | `OCILobLocator *`                                      |
| `REF`                               | `OCIRef *`                                             |
| `RAW`                               | `OCIRaw *`                                             |
| `VARRAY`                            | `OCIArray *` (or `OCIAnyData *` if `is_any` is `TRUE`) |
| `TABLE`                             | `OCITable *` (or `OCIAnyData *` if `is_any` is `TRUE`) |
| `OBJECT`                            | `void *` (or `OCIAnyData *` if `is_any` is `TRUE`)     |

**Related Topics**

- OCIAnyDataBeginCreate()
- OCIAnyDataCollAddElem()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.4 OCIAnyDataBeginCreate()

Allocates an `OCIAnyData` for the given duration and initializes it with the type information.

#### Purpose

Allocates an `OCIAnyData` for the given duration and initializes it with the type information.

#### Syntax

    sword OCIAnyDataBeginCreate ( OCISvcCtx       *svchp,
                                  OCIError        *errhp,
                                  OCITypeCode      tc,
                                  OCIType         *type,
                                  OCIDuration      dur,
                                  OCIAnyData     **sdata );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tc (IN)
Typecode corresponding to `OCIAnyData`. Can be a built-in typecode or a user-defined type's typecode such as:

- `OCI_TYPECODE_OBJECT`

- `OCI_TYPECODE_REF`

- `OCI_TYPECODE_VARRAY`

type (IN)
The type corresponding to `OCIAnyData.` If the typecode corresponds to a built-in type (`OCI_TYPECODE_NUMBER`, and so on), this parameter can be `NULL`. It should be non-`NULL` for user-defined types (`OCI_TYPECODE_OBJECT`, `OCI_TYPECODE_REF`, collection types, and so on).

dur (IN)
Duration for which `OCIAnyData` is allocated. It is one of these:

- A user duration that was previously created. It can be created by using .

- A predefined duration, such as `OCI_DURATION_SESSION`.

sdata (OUT)
Initialized `OCIAnyData`. If `(*sdata)` is not `NULL` at the beginning of the call, the memory could be reused instead of reallocating space for `OCIAnyData`.

Therefore, do not pass an uninitialized pointer here.

#### Comments

`OCIAnyDataBeginCreate()` creates an `OCIAnyData` with an empty skeleton instance. To fill in the attribute values, use `OCIAnyDataAttrSet()` for `OCI_TYPECODE_OBJECT` or `OCIAnyDataCollAddElem()` for the collection typecodes.

Attribute values must be set in order. They must be set from the first attribute to the last. The current attribute number is remembered as state maintained inside the `OCIAnyData`. Piece-wise construction of embedded attributes and collection elements is not yet supported.

For performance reasons, `OCIAnyData` ends up pointing to the `OCIType` parameter passed in. You must ensure that the `OCIType` lives longer (has an allocation duration \>= the duration of `OCIAnyData`, if the `OCIType` is a transient one, or has an allocation or pin duration \>= the duration of `OCIAnyData`, if the `OCIType` is a persistent one).

**Related Topics**

- [OCIDurationBegin()](cartridge-services-memory-services.md)
- OCIAnyDataAttrSet()
- OCIAnyDataCollAddElem()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.5 OCIAnyDataCollAddElem()

Adds the next collection element to the collection attribute of the `OCIAnyData` at the current attribute position.

#### Purpose

If the `OCIAnyData` is of a collection type, then there is no notion of attribute position and this call adds the next collection element.

#### Syntax

    sword OCIAnyDataCollAddElem ( OCISvcCtx    *svchp,
                                  OCIError     *errhp,
                                  OCIAnyData   *sdata,
                                  OCITypeCode   collelem_tc,
                                  OCIType      *collelem_type,
                                  void         *null_ind,
                                  void         *elem_value,
                                  ub4           length,
                                  boolean       is_any,
                                  boolean       last_elem );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN/OUT)
Initialized `OCIAnyData`.

collelem_tc (IN)
The typecode of the collection element to be added. Type checking happens based on `collelem_tc`, `collelem_type` and the type information in the `OCIAnyData`.

collelem_type (IN) \[optional\]
The `collelem_type` parameter gives the type description of the referenced type (for `OCI_TYPECODE_REF`), the type description of the collection type (for `OCI_TYPECODE_NAMEDCOLLECTION`), and the type description of the object (for `OCI_TYPECODE_OBJECT`).

This parameter is not required for built-in typecodes.

null_ind (IN)
Indicates if the `elem_value` is `NULL`. Pass an `(OCIInd *)` for all typecodes except `OCI_TYPECODE_OBJECT`. The indicator should be `OCI_IND_NOTNULL` if the value is not `NULL`, and it should be `OCI_IND_NULL` for a `NULL` value.

If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer to the indicator struct of the `elem_value` as the argument here.

elem_value (IN)
Value for the collection element.

length (IN)
Length of the collection element.

is_any (IN)
Is the attribute in the form of `OCIAnyData`?

last_elem (IN)
Is the element being added the last in the collection?

#### Comments

This call can be invoked for an `OCIAnyData` of type `OCI_TYPECODE_OBJECT` or of any of the collection types. Once piece-wise construction has started for an `OCIAnyData` instance, the `OCIAnyDataConstruct()` calls can no longer be used.

As in `OCIAnyDataAttrSet()`, `is_any` is applicable only if the `collelem_tc` is that of typecode `OCI_TYPECODE_OBJECT` or a collection typecode. If `is_any` is `TRUE`, the attribute should be in the form of `OCIAnyData *`.

If the element being added is the last element in the collection, `last_elem` should be set to `TRUE`.

To add a `NULL` element, the `NULL` indicator (`null_ind`) should be set to `OCI_IND_NULL`, in which case all other arguments are ignored. Otherwise, `null_ind` must be set to `OCI_IND_NOTNULL`.

See `OCIAnyDataAttrSet()` for the type of attribute to be passed in for all the possible types of the collection elements.

**Related Topics**

- OCIAnyDataAttrSet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.6 OCIAnyDataCollGetElem()

Accesses sequentially the elements in the collection attribute at the current position in the `OCIAnyData`.

#### Purpose

Accesses sequentially the elements in the collection attribute at the current position in the `OCIAnyData`.

#### Syntax

    sword OCIAnyDataCollGetElem ( OCISvcCtx    *svchp,
                                  OCIError     *errhp,
                                  OCIAnyData   *sdata,
                                  OCITypeCode   collelem_tc,
                                  OCIType      *collelem_type,
                                  void         *null_ind,
                                  void         *collelem_value,
                                  ub4          *length,
                                  boolean       is_any );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN/OUT)
Initialized `OCIAnyData`.

collelem_tc (IN)
The typecode of the collection element to be retrieved. Type checking happens based on `collelem_tc`, `collelem_type` and the type information in the `OCIAnyData`.

collelem_type (IN) \[optional\]
The `collelem_type` parameter gives the type description of the referenced type (for `OCI_TYPECODE_REF`), the type description of the collection type (for `OCI_TYPECODE_NAMEDCOLLECTION`), and the type description of the object (for `OCI_TYPECODE_OBJECT`).

This parameter is not required for built-in typecodes.

null_ind (OUT)
Indicates if the `collelem_value` is `NULL`. Pass an `(OCIInd *)` for all typecodes except `OCI_TYPECODE_OBJECT`. The indicator should be `OCI_IND_NOTNULL` if the value is not `NULL`, and it should be `OCI_IND_NULL` for a `NULL` value.

If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer `(void **)` to the indicator struct of the `collelem_value` as the argument here.

collelem_value (IN/OUT)
Value for the collection element.

length (IN/OUT)
Length of the collection element. Currently ignored. Set to 0 on input.

is_any (IN)
Is `attr_value` to be returned in the form of `OCIAnyData`?

#### Comments

The `OCIAnyData` data can also correspond to a top-level collection. If the `OCIAnyData` is of type `OCI_TYPECODE_OBJECT`, the attribute at the current position must be a collection of the appropriate type. Otherwise, an error is returned.

As for `OCIAnyDataAttrGet()`, the `is_any` parameter is applicable only if the `collelem_tc` typecode is `OCI_TYPECODE_OBJECT`. If `is_any` is `TRUE`, the `attr_value` is in the form of `OCIAnyData *`.

This call returns `OCI_NO_DATA` when the end of the collection has been reached. It returns `OCI_SUCCESS` upon success and `OCI_ERROR` upon error.

See `OCIAnyDataAttrGet()` for the type of attribute to be passed in for all the possible types of the collection elements.

**Related Topics**

- OCIAnyDataAttrGet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.7 OCIAnyDataConvert()

Constructs an `OCIAnyData` with the given data value that is of the given type.

#### Purpose

You can use this call to construct an entire `OCIAnyData`, which could be of type `OCI_TYPECODE_OBJECT`, any of the collection types, or any of the built-in types.

#### Syntax

    sword OCIAnyDataConvert ( OCISvcCtx    *svchp,
                              OCIError     *errhp,
                              OCITypeCode   tc,
                              OCIType      *inst_type,
                              OCIDuration   dur,
                              void         *null_ind,
                              void         *data_value,
                              ub4           length,
                              OCIAnyData  **sdata );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tc (IN)
Typecode of the data value. Can be a built-in typecode or a user-defined type's typecode (such as `OCI_TYPECODE_OBJECT`, `OCI_TYPECODE_REF`, or `OCI_TYPECODE_VARRAY`).

If (`*sdata`) is not `NULL` and it represents a skeleton instance returned during the `OCIAnyDataSetAddInstance()`, the `tc` and the `inst_type` parameters are optional here. This is because the type information for such a skeleton instance is known. If the `tc` and `inst_type` parameters are provided for this situation, they are used only for type-checking purposes.

inst_type (IN)
Type corresponding to the `OCIAnyData`. If the typecode corresponds to a built-in type (`OCI_TYPECODE_NUMBER`, and so on), this parameter can be `NULL`. It should not be `NULL` for user-defined types (`OCI_TYPECODE_OBJECT`, `OCI_TYPECODE_REF`, or collection types).

dur (IN)
Duration for which the `OCIAnyData` is allocated. It is one of these:

- A user duration that was previously created. It can be created by using `OCIDurationBegin()`.

- A predefined duration, such as `OCI_DURATION_SESSION`.

null_ind
Indicates if `data_value` is `NULL`. Pass an `(OCIInd *)` for all typecodes except `OCI_TYPECODE_OBJECT`. The indicator is `OCI_IND_NOTNULL` if the value is not `NULL`, and it is `OCI_IND_NULL` for a `NULL` value.

If the typecode is `OCI_TYPECODE_OBJECT`, pass a pointer to the indicator struct of the `data_value` as the argument here.

data_value (IN)
The data value (should be of the type with which the `OCIAnyData` was initialized). See `OCIAnyDataAttrSet()` for the appropriate C type corresponding to each allowed typecode.

length (IN)
Currently, this parameter is ignored. Pass 0 here. In the future, this may be used for certain typecodes where the data representation itself does not give the length implicitly.

sdata (IN/OUT)
Initialized `OCIAnyData`. If (`*sdata`) is not `NULL` at the beginning of the call, the memory could be reused instead of reallocating space for `OCIAnyData`.

Therefore, do not pass an uninitialized pointer here.

If (`*sdata`) represents a skeleton instance returned during an `OCIAnyDataSetAddInstance()` call, the `tc` and `inst_type` parameters are used for type checking, if necessary.

#### Comments

For performance reasons, `OCIAnyData` pointer ends up pointing to the passed in `OCIType` parameter. You must ensure that the `OCIType` lives longer (has an allocation duration \>= the duration of `OCIAnyData`, if the `OCIType` is a transient one, or has an allocation or pin duration \>= the duration of `OCIAnyData,` if the `OCIType` is a persistent one).

**Related Topics**

- [OCIAnyDataSetAddInstance()](oci-any-data-set-interface-functions.md)
- OCIAnyDataAttrSet()
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.8 OCIAnyDataDestroy()

Free an OCIAnyData.

#### Purpose

Frees an `OCIAnyData`.

#### Syntax

    sword OCIAnyDataDestroy ( OCISvcCtx      *svchp,
                              OCIError       *errhp,
                              OCIAnyData     *sdata );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN/OUT)
Pointer to a type of `OCIAnyData` to be freed.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.9 OCIAnyDataEndCreate()

Marks the end of `OCIAnyData` creation.

#### Purpose

It should be called after initializing all attributes of its instances with suitable values. This call is valid only if `OCIAnyDataBeginCreate()` was called earlier for the `OCIAnyData`.

#### Syntax

    sword OCIAnyDataEndCreate ( OCISvcCtx      *svchp,
                                OCIError       *errhp,
                                OCIAnyData     *data );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

data (IN/OUT)
Initialized `OCIAnyData`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.10 OCIAnyDataGetCurrAttrNum()

Returns the current attribute number of `OCIAnyData`.

#### Purpose

If `OCIAnyData` is being constructed, this function refers to the current attribute that is being set. Otherwise, if `OCIAnyData` is being accessed, this function refers to the attribute that is being accessed.

#### Syntax

    sword OCIAnyDataGetCurrAttrNum( OCISvcCtx      *svchp,
                                    OCIError       *errhp,
                                    OCIAnyData     *sdata,
                                    ub4            *attrnum );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN)
Initialized `OCIAnyData`.

attrnum (OUT)
The attribute number.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.11 OCIAnyDataGetType()

Gets the type corresponding to an `OCIAnyData` value.

#### Purpose

It returns the actual pointer to the type maintained inside an `OCIAnyData`. No copying is done for performance reasons. Do not use this type after the `OCIAnyData` is freed (or its duration ends).

#### Syntax

    sword OCIAnyDataGetType( OCISvcCtx      *svchp,
                             OCIError       *errhp,
                             OCIAnyData     *data,
                             OCITypeCode    *tc,
                             OCIType       **type );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

data (IN)
Initialized `OCIAnyData`.

tc (OUT)
The typecode corresponding to the `OCIAnyData`.

type (OUT)
The type corresponding to the `OCIAnyData`. This is `NULL` if the `OCIAnyData` corresponds to a built-in type.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.12 OCIAnyDataIsNull()

Checks if the content of the type within the `OCIAnyData` is `NULL`.

#### Purpose

Checks if the content of the type within the `OCIAnyData` is `NULL`.

#### Syntax

    sword OCIAnyDataIsNull ( OCISvcCtx         *svchp,
                             OCIError          *errhp,
                             const OCIAnyData  *sdata,
                             boolean           *isNull) ;

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err` and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

sdata (IN)
`OCIAnyData` to be checked.

isNull (IN/OUT)
`TRUE` if `NULL`; otherwise, `FALSE`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.3.13 OCIAnyDataTypeCodeToSqlt()

Converts the `OCITypeCode` for an AnyData value to the SQLT code that corresponds to the representation of the value as returned by the OCIAnyData API.

#### Purpose

Converts the `OCITypeCode` for an `OCIAnyData` value to the SQLT code that corresponds to the representation of the value as returned by the OCIAnyData API.

#### Syntax

    sword  OCIAnyDataTypeCodeToSqlt ( OCIError       *errhp,
                                      OCITypeCode     tc,
                                      ub1            *sqltcode,
                                      ub1            *csfrm) ;

#### Parameters

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `errhp`, and this function returns `OCI_ERROR`. Diagnostic information can be obtained by calling `OCIErrorGet()`.

tc (IN)
`OCITypeCode` corresponding to the AnyData value.

sqltcode (OUT)
SQLT code corresponding to the user format of the typecode.

csfrm (OUT)
Charset form corresponding to the user format of the typecode. Meaningful only for character types. Returns `SQLCS_IMPLICIT` or `SQLCS_NCHAR` (for `NCHAR` types).

#### Comments

This function converts `OCI_TYPECODE_CHAR` and `OCI_TYPECODE_VARCHAR2` to `SQLT_VST` (which corresponds to the `OCIString` mapping) with a charset form of `SQLCS_IMPLICIT`. `OCI_TYPECODE_NVARCHAR2` also returns `SQLT_VST` (`OCIString` mapping is used by the OCIAnyData API) with a charset form of `SQLCS_NCHAR`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
- [NCHAR Typecodes for OCIAnyData Functions](object-relational-data-types-in-oci.md)
