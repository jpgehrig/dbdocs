Oracle Database for Windows stores its configuration information in a repository (the registry) that is organized in a tree format.

The tree format consists of keys in the registry and parameter values for the keys. Keys and parameter values can be viewed and modified in Registry Editor.

Keys are folders that appear in the left pane of a Registry Editor window. A key contains subkeys or parameters.

**Note:**

Although Registry Editor lets you view and modify registry keys and parameter values, you typically are not required to do so. In fact, you can render your system useless if you make incorrect changes. Therefore, only advanced users must edit the registry. Back up your system before making any changes in the registry.

Parameters in the Registry Editor appear as a string, consisting of three components:

- Parameter name

- Value class or type of entry

- Value itself

For example, parameter `ORACLE_SID` can have the following entry in the registry:

    ORACLE_SID:reg_sz:orcl1

Value classes for Oracle Database for Windows parameters are:

- String value with a `REG_SZ`, `REG_EXPAND_SZ` (for an expandable string), or a `REG_MULTI_SZ` (for multiple strings) prefix to identify a parameter value entry as a data string

- Binary value with a `REG_BINARY`, `REG_DWORD` or `REG_QWORD` prefix to identify a value entry as a `dword` or `qword `(hexadecimal data) entry

Most Oracle Database for the Windows parameter values are string types. Use Oracle Universal Installer defaults when a type is not given.

**Parent topic:** [Configuration Parameters and the Registry](configuration-parameters-and-registry.md)
