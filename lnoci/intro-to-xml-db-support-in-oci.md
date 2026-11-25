This chapter describes the XML DB functions in detail.

**See Also:**

[OCI Support for XML](oci-support-for-xml.md)

### 32.1.1 Conventions for OCI Functions

Describes conventions used in describing each function.

See the [Conventions for OCI Functions](introduction-to-relational-functions.md) for the conventions used in describing each function. The entries for each function may also contain the following information:

### 32.1.2 Returns

Describes the function return values.

Unless otherwise stated, the function returns the values described in Table 32-1.

Table 32-1 Function Return Values

| Return Value         | Meaning                                                                                                                          |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `OCI_SUCCESS`        | The operation succeeded.                                                                                                         |
| `OCI_ERROR`          | The operation failed. The specific error can be retrieved by calling `OCIErrorGet()` on the error handle passed to the function. |
| `OCI_INVALID_HANDLE` | The OCI handle passed to the function is invalid.                                                                                |

**See Also:**

[Error Handling in OCI](oci-programming-basics.md) for more information about return codes and error handling
