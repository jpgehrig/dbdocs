This section introduces the OCI external procedure functions.

These functions enable users of external procedures to raise errors, allocate some memory, and get OCI context information.

Then the cartridge services functions are described.

**See Also:**

- [Oracle Database Development Guide](../adfns/external-procedures.md) for more information about using these functions in external procedures

- [Oracle Database Data Cartridge Developer's Guide](../addci/cartridge-services-using-C-CPP-and-java.md) for more information about using these functions

### 29.1.1 Conventions for OCI Functions

Describes conventions used in describing each function.

See the [Conventions for OCI Functions](introduction-to-relational-functions.md) for the conventions used in describing each function. The entries for each function may also contain the following information:

- Return Codes

- With_Context Type

#### Return Codes

Success and error return codes are defined for certain external procedure interface functions. If a particular interface function returns `OCIEXTPROC_SUCCESS` or `OCIEXTPROC_ERROR`, then applications must use these macros to check for return values.

- `OCIEXTPROC_SUCCESS` - External Procedure Success Return Code

- `OCIEXTPROC_ERROR` - External Procedure Failure Return Code

#### With_Context Type

The C callable interface to PL/SQL external procedures requires the `with_context` parameter to be passed. The type of this structure is `OCIExtProcContext`, which is opaque to the user.

The user can declare the `with_context` parameter in the application as follows:

    OCIExtProcContext *with_context;
