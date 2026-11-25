This section describes the globalization support functions in detail.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

### 31.1.1 Conventions for OCI Functions

Describes the conventions for OCI functions.

The entries for each function may also contain the following information:

- Returns — The values returned. The standard return values have the following meanings as described in the following table.

Table 31-1 Function Return Values

| Return Value         | Meaning                                                                                                                          |
|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `OCI_SUCCESS`        | The operation succeeded.                                                                                                         |
| `OCI_ERROR`          | The operation failed. The specific error can be retrieved by calling `OCIErrorGet()` on the error handle passed to the function. |
| `OCI_INVALID_HANDLE` | The OCI handle passed to the function is invalid.                                                                                |

**See Also:**

- [Conventions for OCI Functions](introduction-to-relational-functions.md)for the conventions used in describing each function

- [Error Handling in OCI](oci-programming-basics.md) for more information about return codes and error handling
