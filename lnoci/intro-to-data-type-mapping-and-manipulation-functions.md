Introduces detailed information about OCI data type mapping and manipulation functions.

This section describes the OCI data type mapping and manipulation functions in detail.

**See Also:**

[Object-Relational Data Types in OCI](object-relational-data-types-in-oci.md) for more information about the functions listed in this chapter

### 28.1.1 Conventions for OCI Functions

Reports the conventions used for describing OCI functions.

See the [Conventions for OCI Functions](introduction-to-relational-functions.md) for the conventions used in describing each function. The entries for each function may also contain the following information:

### 28.1.2 Returns

Describes the value returned by the function.

A description of what value is returned by the function if the function returns something other than the standard return codes listed in "Table 28-1".

### 28.1.3 Data Type Mapping and Manipulation Function Return Values

Describes the function return values.

The OCI data type mapping and manipulation functions typically return one of the values shown in Table 28-1.

Table 28-1 Function Return Values

| Return Value         | Meaning                                                                                                                          |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `OCI_SUCCESS`        | The operation succeeded.                                                                                                         |
| `OCI_ERROR`          | The operation failed. The specific error can be retrieved by calling `OCIErrorGet()` on the error handle passed to the function. |
| `OCI_INVALID_HANDLE` | The OCI handle passed to the function is invalid.                                                                                |

**See Also:**

[Error Handling in OCI](oci-programming-basics.md) for more information about return codes and error handling

### 28.1.4 Functions Returning Other Values

Lists functions returning values directly from the function call.

Some functions return values other than those listed in Table 28-1. When you use the following functions, consider that they return a value directly from the function call, rather than through an OUT parameter.

- [OCICollMax()](oci-collection-and-iterator-functions.md)

- [OCIRawPtr()](oci-raw-functions.md)

- [OCIRawSize()](oci-raw-functions.md)

- [OCIRefHexSize()](oci-REF-functions.md)

- [OCIRefIsEqual()](oci-REF-functions.md)

- [OCIRefIsNull()](oci-REF-functions.md)

- [OCIStringPtr()](oci-string-functions.md)

- [OCIStringSize()](oci-string-functions.md)

### 28.1.5 Server Round-Trips for Data Type Mapping and Manipulation Functions

Indicates the number of server round-trips required for individual OCI data type mapping and manipulation functions.

For a table showing the number of server round-trips required for individual OCI data type mapping and manipulation functions, see [Table C-5](oci-function-server-round-trips.md).

### 28.1.6 Examples

Describes information about the examples.

For more information about these functions, including some code examples, see [Object-Relational Data Types in OCI](object-relational-data-types-in-oci.md).
