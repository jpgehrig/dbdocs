Table 30-2 lists the Type Interface functions that are described in this section.

Table 30-2 Type Interface Functions

| Function               | Purpose                                                                                                                                                 |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| OCITypeAddAttr()       | Add an attribute to an object type that was constructed earlier with typecode `OCI_TYPECODE_OBJECT`                                                     |
| OCITypeBeginCreate()   | Begin the construction process for a transient type. The type is anonymous (no name).                                                                   |
| OCITypeEndCreate()     | Finish construction of a type description. Subsequently, only access is allowed.                                                                        |
| OCITypeSetBuiltin()    | Set built-in type information. This call can be made only if the type has been constructed with a built-in typecode (`OCI_TYPECODE_NUMBER`, and so on). |
| OCITypeSetCollection() | Set collection type information. This call can be made only if the type has been constructed with a collection typecode.                                |

### 30.2.1 OCITypeAddAttr()

Adds an attribute to an object type that was constructed earlier with typecode `OCI_TYPECODE_OBJECT`.

#### Purpose

Adds an attribute to an object type that was constructed earlier with typecode `OCI_TYPECODE_OBJECT`.

#### Syntax

    sword OCITypeAddAttr ( OCISvcCtx   *svchp,
                           OCIError    *errhp,
                           OCIType     *type,
                           const text  *a_name,
                           ub4          a_length,
                           OCIParam    *attr_info );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

type (IN/OUT)
The type description that is being constructed.

a_name (IN) \[optional\]
The name of the attribute.

a_length (IN) \[optional\]
The length of the attribute name, in bytes.

attr_info (IN)
Information about the attribute. It is obtained by allocating an `OCIParam` parameter handle and setting type information in the `OCIParam` using `OCIAttrSet()` calls.

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.2.2 OCITypeBeginCreate()

Begins the construction process for a transient type. The type is anonymous (no name).

#### Purpose

Begins the construction process for a transient type. The type is anonymous (no name).

#### Syntax

    sword OCITypeBeginCreate ( OCISvcCtx     *svchp,
                               OCIError      *errhp,
                               OCITypeCode    tc,
                               OCIDuration    dur,
                               OCIType      **type );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

tc (IN)
The typecode for the type. The typecode could correspond to an object type or a built-in type.

Currently, the permissible values for user defined types are:

- `OCI_TYPECODE_OBJECT` for an object type (structured)

- `OCI_TYPECODE_VARRAY` for a `VARRAY` collection type

- `OCI_TYPECODE_TABLE` for a nested table collection type

For object types, call `OCITypeAddAttr()` to add each of the attribute types. For collection types, call `OCITypeSetCollection()`. Subsequently, call `OCITypeEndCreate()` to finish the creation process.

The permissible values for built-in typecodes are specified in "[Typecodes](data-types.md)". Additional information about built-in types (precision, scale for numbers, character set information for `VARCHAR2`s, and so on) if any, must be set with a subsequent call to `OCITypeSetBuiltin()`. Finally, you must use `OCITypeEndCreate()` to finish the creation process.

dur (IN)
The allocation duration for the type. It is one of these:

- A user duration that was previously created. It can be created by using `OCIDurationBegin()`.

- A predefined duration, such as `OCI_DURATION_SESSION`.

type (OUT)
The `OCIType` (Type Descriptor) that is being constructed.

#### Comments

To create a persistent named type, use the SQL statement `CREATE` `TYPE`. Transient types have no identity. They are pure values.

**Related Topics**

- OCITypeAddAttr()
- OCITypeSetCollection()
- OCITypeEndCreate()
- OCITypeSetBuiltin()
- [OCIDurationBegin()](cartridge-services-memory-services.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.2.3 OCITypeEndCreate()

Finishes construction of a type description. Subsequently, only access is allowed.

#### Purpose

Finishes construction of a type description. Subsequently, only access is allowed.

#### Syntax

    sword OCITypeEndCreate ( OCISvcCtx  *svchp,
                             OCIError   *errhp,
                             OCIType    *type );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

type (IN/OUT)
The type description that is being constructed.

**Related Topics**

- [OCIErrorGet()](miscellaneous-functions.md)

### 30.2.4 OCITypeSetBuiltin()

Sets built-in type information.

#### Purpose

This call can be made only if the type has been constructed with a built-in typecode (`OCI_TYPECODE_NUMBER`, and so on).

#### Syntax

    sword OCITypeSetBuiltin ( OCISvcCtx   *svchp,
                              OCIError    *errhp,
                              OCIType     *type,
                              OCIParam    *builtin_info );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

type (IN/OUT)
The type description that is being constructed.

builtin_info (IN)
Provides information about the built-in type (precision, scale, character set, and so on). It is obtained by allocating an `OCIParam` parameter handle and setting type information in the `OCIParam` using `OCIAttrSet()` calls.

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)

### 30.2.5 OCITypeSetCollection()

Sets collection type information.

#### Purpose

This call can be made only if the type has been constructed with a collection typecode.

#### Syntax

    sword OCITypeSetCollection ( OCISvcCtx   *svchp,
                                 OCIError    *errhp,
                                 OCIType     *type,
                                 OCIParam    *collelem_info,
                                 ub4          coll_count );

#### Parameters

svchp (IN)
The OCI service context.

errhp (IN/OUT)
The OCI error handle. If there is an error, it is recorded in `err`, and this function returns `OCI_ERROR`. Obtain diagnostic information by calling `OCIErrorGet()`.

type (IN/OUT)
The type descriptor that is being constructed.

collelem_info (IN)
`collelem_info` provides information about the collection element. It is obtained by allocating an `OCIParam` parameter handle and setting type information in the `OCIParam` using `OCIAttrSet()` calls.

coll_count (IN)
The count of elements in the collection. Pass 0 for a nested table (which is unbounded).

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIErrorGet()](miscellaneous-functions.md)
