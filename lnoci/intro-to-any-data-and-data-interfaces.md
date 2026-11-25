This section describes the OCI Any Type and Data functions in detail.

**See Also:**

"[AnyType, AnyData, and AnyDataSet Interfaces](object-relational-data-types-in-oci.md)"

### 30.1.1 Conventions for OCI Functions

Describes the conventions for OCI functions. The entries for each function may also contain function return values.

See the [Conventions for OCI Functions](introduction-to-relational-functions.md) for the conventions used in describing each function.

The OCI Any Type and Data functions typically return one of the values described in the following table.

Table 30-1 Function Return Values

| Return Value         | Meaning                                                                                                                          |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `OCI_SUCCESS`        | The operation succeeded.                                                                                                         |
| `OCI_ERROR`          | The operation failed. The specific error can be retrieved by calling `OCIErrorGet()` on the error handle passed to the function. |
| `OCI_INVALID_HANDLE` | The OCI handle passed to the function is invalid.                                                                                |

**See Also:**

[Error Handling in OCI](oci-programming-basics.md) for more information about return codes and error handling
