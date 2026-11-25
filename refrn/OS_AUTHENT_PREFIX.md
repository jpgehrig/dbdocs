## 1.263 OS_AUTHENT_PREFIX

`OS_AUTHENT_PREFIX` specifies a prefix that Oracle Database uses to authenticate users attempting to connect to the server.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | String                                        |
| Syntax              | `OS_AUTHENT_PREFIX = ``authentication_prefix` |
| Default value       | `OPS$`                                        |
| Modifiable          | No                                            |
| Modifiable in a PDB | No                                            |
| Basic               | No                                            |

Oracle Database concatenates the value of this parameter to the beginning of the user's operating system account name. When a connection request is attempted, Oracle Database compares the prefixed username with Oracle user names in the database.

The default value of this parameter is `OPS$` for backward compatibility with previous versions. However, you might prefer to set the prefix value to "" (a null string), thereby eliminating the addition of any prefix to operating system account names.

**Note:**

The text of the `OS_AUTHENT_PREFIX` parameter is case sensitive on some operating systems.

**See Also:**

- [Oracle Database Security Guide](../dbseg/customizing-the-use-of-strong-authentication.md) for more information on setting this parameter

- Your operating system-specific Oracle documentation for the default value
