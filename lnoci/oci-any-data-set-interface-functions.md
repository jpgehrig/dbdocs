Lists and describes OCI Any Data set interface functions.

Table 30-6 lists the Any Data Set Interface functions that are described in this section.

Table 30-6 Any Data Set Functions

| Function                   | Purpose                                                                                                      |
|:---------------------------|:-------------------------------------------------------------------------------------------------------------|
| OCIAnyDataSetAddInstance() | Add a new skeleton instance to the `OCIAnyDataSet` and set all the attributes of the instance to `NULL`      |
| OCIAnyDataSetBeginCreate() | Allocate an `OCIAnyDataSet` for the given duration and initialize it with the type information               |
| OCIAnyDataSetDestroy()     | Free the `OCIAnyDataSet`                                                                                     |
| OCIAnyDataSetEndCreate()   | Mark the end of `OCIAnyDataSet` creation                                                                     |
| OCIAnyDataSetGetCount()    | Get the number of instances in the `OCIAnyDataSet`                                                           |
| OCIAnyDataSetGetInstance() | Return the `OCIAnyData` corresponding to an instance at the current position and update the current position |
| OCIAnyDataSetGetType()     | Get the type corresponding to an `OCIAnyDataSet`                                                             |

### 30.4.1 OCIAnyDataSetAddInstance()

Adds a new skeleton instance to the `OCIAnyDataSet` and sets all the attributes of the instance to `NULL`.

#### Purpose

Adds a new skeleton instance to the `OCIAnyDataSet` and sets all the attributes of the instance to `NULL`.

#### Syntax

    sword OCIAnyDataSetAddInstance ( OCISvcCtx       *svchp,
                                     OCIError        *errhp,
                                     OCIAnyDataSet   *data_set,
                                     OCIAnyData     **data );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

data_set (IN/OUT)
`OCIAnyDataSet` to which a new instance is added.

data (IN/OUT)
`OCIAnyData` corresponding to the newly added instance. If `(*data)` is `NULL`, a new `OCIAnyData` is allocated for the same duration as the `OCIAnyDataSet`. If `(*data)` is not `NULL`, it is reused. This `OCIAnyData` can be subsequently constructed using the `OCIAnyDataConvert()` call, or it can be constructed piece-wise using the `OCIAnyDataAttrSet()` or the `OCIAnyDataCollAddElem()` calls.

#### Comments

This call returns this skeleton instance through the `OCIAnyData` parameter that can be constructed subsequently by invoking the OCIAnyData API.

**Note:**

The old value is not destroyed. You must destroy the old value pointed to by (`*data`) and set (`*data`) to a `NULL` pointer before beginning to make a sequence of these calls. No deep copying (of `OCIType` information or of the data part) is done in the returned `OCIAnyData`. This `OCIAnyData` cannot be used beyond the allocation duration of the `OCIAnyDataSet` (it is like a reference into the `OCIAnyDataSet`). The returned `OCIAnyData` can be reused on subsequent calls to this function, to sequentially add new data instances to the `OCIAnyDataSet`.

**Related Topics**

- [OCIAnyDataConvert()](oci-any-data-interface-functions.md)
- [OCIAnyDataAttrSet()](oci-any-data-interface-functions.md)
- [OCIAnyDataCollAddElem()](oci-any-data-interface-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.2 OCIAnyDataSetBeginCreate()

Allocates an `OCIAnyDataSet` for the given duration and initializes it with the type information.

#### Purpose

The `OCIAnyDataSet` can hold multiple instances of the given type.

#### Syntax

    sword OCIAnyDataSetBeginCreate ( OCISvcCtx       *svchp,
                                     OCIError        *errhp,
                                     OCITypeCode      typecode,
                                     const OCIType   *type,
                                     OCIDuration      dur,
                                     OCIAnyDataSet  **data_set );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

typecode (IN)
Typecode corresponding to the `OCIAnyDataSet`.

type (IN)
Type corresponding to the `OCIAnyDataSet`. If the typecode corresponds to a built-in type, such as `OCI_TYPECODE_NUMBER`, this parameter can be `NULL`. It should be non-`NULL` for user-defined types, such as `OCI_TYPECODE_OBJECT`, `OCI_TYPECODE_REF`, and collection types.

dur (IN)
Duration for which `OCIAnyDataSet` is allocated. It is one of these:

- A user duration that was previously created. It can be created by using `OCIDurationBegin()`.

- A predefined duration, such as `OCI_DURATION_SESSION`.

data_set (OUT)
Initialized `OCIAnyDataSet`.

#### Comments

For performance reasons, the `OCIAnyDataSet` ends up pointing to the `OCIType` parameter passed in. You must ensure that the `OCIType` lives longer (has an allocation duration \>= the duration of the `OCIAnyData` if the `OCIType` is a transient one, or has allocation or pin duration \>= the duration of the `OCIAnyData`, if the `OCIType` is a persistent one).

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.3 OCIAnyDataSetDestroy()

Frees the `OCIAnyDataSet`.

#### Purpose

Frees the `OCIAnyDataSet`.

#### Syntax

    sword OCIAnyDataSetDestroy ( OCISvcCtx      *svchp,
                                 OCIError       *errhp,
                                 OCIAnyDataSet  *data_set );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCI_ERROR`.

data_set (IN/OUT)
`OCIAnyDataSet` to be freed.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.4 OCIAnyDataSetEndCreate()

Marks the end of `OCIAnyDataSet` creation.

#### Purpose

This function should be called after constructing all of its instances.

#### Syntax

    sword OCIAnyDataSetEndCreate ( OCISvcCtx      *svchp,
                                   OCIError       *errhp,
                                   OCIAnyDataSet  *data_set );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCI_ERROR`.

data_set (IN/OUT)
Initialized `OCIAnyDataSet`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.5 OCIAnyDataSetGetCount()

Gets the number of instances in the `OCIAnyDataSet`.

#### Purpose

Gets the number of instances in the `OCIAnyDataSet`.

#### Syntax

    sword OCIAnyDataSetGetCount( OCISvcCtx      *svchp,
                                 OCIError       *errhp,
                                 OCIAnyDataSet  *data_set,
                                 ub4            *count );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCI_ERROR`.

data_set (IN/OUT)
A well-formed `OCIAnyDataSet`.

count (OUT)
Number of instances in `OCIAnyDataSet`.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.6 OCIAnyDataSetGetInstance()

Returns the `OCIAnyData` corresponding to an instance at the current position and updates the current position.

#### Purpose

Returns the `OCIAnyData` corresponding to an instance at the current position and updates the current position.

#### Syntax

    sword OCIAnyDataSetGetInstance ( OCISvcCtx      *svchp,
                                     OCIError       *errhp,
                                     OCIAnyDataSet  *data_set,
                                     OCIAnyData    **data );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCI_ERROR`.

data_set (IN/OUT)
A well-formed `OCIAnyDataSet`.

data (IN/OUT)
`OCIAnyDat`a corresponding to the instance. If (\*data) is `NULL`, a new `OCIAnyData` is allocated for same duration as the `OCIAnyDataSet`. If (`*data`) is not `NULL`, it is reused.

#### Comments

Only sequential access to the instances in an `OCIAnyDataSet` is allowed. This call returns the `OCIAnyData` corresponding to an instance at the current position and updates the current position. Subsequently, the `OCIAnyData` access routines can be used to access the instance.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.4.7 OCIAnyDataSetGetType()

Gets the type corresponding to an `OCIAnyDataSet`.

#### Purpose

Gets the type corresponding to an `OCIAnyDataSet`.

#### Syntax

    sword OCIAnyDataSetGetType ( OCISvcCtx      *svchp,
                                 OCIError       *errhp,
                                 OCIAnyDataSet  *data_set,
                                 OCITypeCode    *tc,
                                 OCIType       **type );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCI_ERROR`.

data_set (IN)
Initialized `OCIAnyDataSet`.

tc (OUT)
The typecode corresponding to the type of the `OCIAnyDataSet`.

type (OUT)
The type corresponding to the `OCIAnyDataSet`. This is `NULL` if the `OCIAnyData` corresponds to a built-in type.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)
