## 1.321 SEC_MAX_FAILED_LOGIN_ATTEMPTS

`SEC_MAX_FAILED_LOGIN_ATTEMPTS` specifies the number of authentication attempts that can be made by a client on a connection to the server process.

| Property            | Description                              |
|:--------------------|:-----------------------------------------|
| Parameter type      | Integer                                  |
| Default value       | `3`                                      |
| Modifiable          | No                                       |
| Modifiable in a PDB | No                                       |
| Range of values     | An integer greater than or equal to `1`. |
| Basic               | No                                       |

These login attempts can be for multiple user accounts in the same connection. After the specified number of failure attempts, the connection will be automatically dropped by the server process, and the server process is terminated.

**See Also:**

[Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for more information about this parameter
