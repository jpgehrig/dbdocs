Introduces OCI relational function calls.

This chapter and [More Oracle Database Access C API](more-database-access-c-api.md) describe the OCI relational function calls and cover the functions in the basic OCI.

**See Also:**

[Error Handling in OCI](oci-programming-basics.md) for information about return codes and error handling

### 25.1.1 Conventions for OCI Functions

Introduces the conventions used for OCI functions.

For each function, the following information is listed:

### 25.1.2 Purpose

What is the functions purpose?

A brief description of the action performed by the function.

### 25.1.3 Syntax

What is the function declaration?

The function declaration.

### 25.1.4 Parameters

A description of each of the function's parameters and their modes.

This description includes the parameter's mode. The mode of a parameter has three possible values, as described in Table 25-1.

Table 25-1 Mode of a Parameter

| Mode   | Description                                                                                             |
|:-------|:--------------------------------------------------------------------------------------------------------|
| IN     | A parameter that passes data to the OCI                                                                 |
| OUT    | A parameter that receives data from the OCI on this call                                                |
| IN/OUT | A parameter that passes data on the call and receives data on the return from this or a subsequent call |

### 25.1.5 Comments

Describes more detailed information about the function (if available).

This information may include restrictions on the use of the function, or other information that might be useful when using the function in an application.

### 25.1.6 Returns

This optional section describes the possible values that can be returned.

This section can be found either before or after the Comments section.

### 25.1.7 Example

Provides acomplete or partial code example demonstrating the use of the function call being described.

Not all function descriptions include an example.

### 25.1.8 Related Functions

Shows a list of related function calls to the function if applicable.

A list of related function calls.

### 25.1.9 About Calling OCI Functions

Provides useful information about calling OCI functions.

Unlike earlier versions of OCI, in and after release 8, you cannot pass -1 for the string length parameter of a `NULL`-terminated string. When you pass string lengths as parameters, do not include the `NULL` terminator byte in the length. The OCI does not expect strings to be `NULL`-terminated.

Buffer lengths that are OCI parameters are in bytes, with the following exceptions:

- The `amount` parameters in some LOB calls are in characters

- When `UTF-16` encoding of text is used in function parameters, the length is in character points

### 25.1.10 Server Round-Trips for LOB Functions

Indicates the number of server round-trips required for individual OCI LOB functions.

For a table showing the number of server round-trips required for individual OCI LOB functions, see [OCI Function Server Round-Trips](oci-function-server-round-trips.md).
