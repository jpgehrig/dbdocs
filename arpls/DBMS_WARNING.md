## 192  DBMS_WARNING

The `DBMS_WARNING` package provides a way to manipulate the behavior of PL/SQL warning messages, in particular by reading and changing the setting of the `PLSQL_WARNINGS` initialization parameter to control what kinds of warnings are suppressed, displayed, or treated as errors. This package provides the interface to query, modify and delete current system or session settings.

This chapter contains the following topics:

- Security Model

- Summary of DBMS_WARNING Subprograms

### 192.1 DBMS_WARNING Security Model

Note that for all the following interfaces, if value of the scope parameter is `SYSTEM`, then the user must have `ALTER` `SYSTEM` privilege.

### 192.2 Summary of DBMS_WARNING Subprograms

This table lists the `DBMS_WARNING` subprograms and briefly describes them.

Table 192-1 DBMS_WARNING Package Subprograms

| Subprogram                           | Description                                                                                                |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| ADD_WARNING_SETTING_CAT Procedure    | Modifies the current `session` or `system` warning settings of the `warning_category` previously supplied  |
| ADD_WARNING_SETTING_NUM Procedure    | Modifies the current `session` or `system` warning settings of the or `warning_number` previously supplied |
| GET_CATEGORY Function                | Returns the category name, given the message number                                                        |
| GET_WARNING_SETTING_CAT Function     | Returns the specific warning category in the session                                                       |
| GET_WARNING_SETTING_NUM Function     | Returns the specific warning number in the session                                                         |
| GET_WARNING_SETTING_STRING Function  | Returns the entire warning string for the current session                                                  |
| SET_WARNING_SETTING_STRING Procedure | Replaces previous settings with the new value                                                              |

#### 192.2.1 ADD_WARNING_SETTING_CAT Procedure

You can modify the current session's or system's warning settings with the value supplied in this procedure. The value will be added to the existing parameter setting if the value for the `warning_category` or `warning_value` has not been set, or override the existing value.

The effect of calling this function is same as adding the qualifier (`ENABLE`/`DISABLE`/`ERROR`) on the category specified to the end of the current session or system setting.

##### Syntax

    DBMS_WARNING.ADD_WARNING_SETTING_CAT (
       warning_category    IN    VARCHAR2,
       warning_value       IN    VARCHAR2,
       scope               IN    VARCHAR2);

##### Parameters

Table 192-2 ADD_WARNING_SETTING_CAT Procedure Parameters

| Parameter          | Description                                                                                                                          |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `warning_category` | Name of the category. Allowed values are `ALL`, `INFORMATIONAL`, `SEVERE` and `PERFORMANCE`.                                         |
| `warning_value`    | Value for the category. Allowed values are `ENABLE`, `DISABLE`, and `ERROR`.                                                         |
| `scope`            | Specifies if the changes are being performed in the session context or the system context. Allowed values are `SESSION` or `SYSTEM`. |

#### 192.2.2 ADD_WARNING_SETTING_NUM Procedure

You can modify the current `session` or `system` warning settings with the value supplied in this procedure. If the value was already set, you will override the existing value.

The effect of calling this function is same as adding the qualifier (`ENABLE` / `DISABLE`/ `ERROR`) on the category specified to the end of the current session or system setting.

##### Syntax

    DBMS_WARNING.ADD_WARNING_SETTING_NUM (
       warning_number      IN    NUMBER,
       warning_value       IN    VARCHAR2,
       scope               IN    VARCHAR2);

##### Parameters

Table 192-3 ADD_WARNING_SETTING_NUM Procedure Parameters

| Parameter        | Description                                                                                                                          |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `warning_number` | The warning number. Allowed values are all valid warning numbers.                                                                    |
| `warning_value`  | Value for the category. Allowed values are `ENABLE`, `DISABLE`, and `ERROR`.                                                         |
| `scope`          | Specifies if the changes are being performed in the session context or the system context. Allowed values are `SESSION` or `SYSTEM`. |

Example 192-1 Enabling the Deprecation Warnings

This example shows how to enable the `DEPRECATE` pragma warnings using the DBMS_WARNING package for the session.

    BEGIN
      DBMS_WARNING.ADD_WARNING_SETTING_NUM (6019,
                                            'ENABLE',
                                            'SESSION');

      DBMS_WARNING.ADD_WARNING_SETTING_NUM (6020,
                                            'ENABLE',
                                            'SESSION');

      DBMS_WARNING.ADD_WARNING_SETTING_NUM (6021,
                                            'ENABLE',
                                            'SESSION');

      DBMS_WARNING.ADD_WARNING_SETTING_NUM (6022,
                                            'ENABLE',
                                            'SESSION');
    END;

#### 192.2.3 GET_CATEGORY Function

This function returns the category name, given the message number.

##### Syntax

    DBMS_WARNING.GET_CATEGORY (
       warning_number  IN   pls_integer)
    RETURN VARCHAR2;

##### Parameters

Table 192-4 GET_CATEGORY Function Parameters

| Parameter        | Description                 |
|:-----------------|:----------------------------|
| `warning_number` | The warning message number. |

#### 192.2.4 GET_WARNING_SETTING_CAT Function

This function returns the specific warning category setting for the current session.

##### Syntax

    DBMS_WARNING.GET_WARNING_SETTING_CAT (
       warning_category    IN    VARCHAR2)
    RETURN warning_value;

##### Parameters

Table 192-5 GET_WARNING_SETTING_CAT Function Parameters

| Parameter          | Description                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------|
| `warning_category` | Name of the category. Allowed values are all valid category names (`ALL`, `INFORMATIONAL`, `SEVERE` and `PERFORMANCE`). |

#### 192.2.5 GET_WARNING_SETTING_NUM Function

This function returns the specific warning number setting for the current session.

##### Syntax

    DBMS_WARNING.GET_WARNING_SETTING_NUM (
       warning_number      IN    NUMBER)
    RETURN warning_value;

##### Parameters

Table 192-6 GET_WARNING_SETTING_NUM Function Parameters

| Parameter        | Description                                                   |
|:-----------------|:--------------------------------------------------------------|
| `warning_number` | Warning number. Allowed values are all valid warning numbers. |

#### 192.2.6 GET_WARNING_SETTING_STRING Function

This function returns the entire warning string for the current session.

##### Syntax

    DBMS_WARNING.GET_WARNING_SETTING_STRING
     RETURN VARCHAR2;

##### Usage Notes

Use this function when you do not have `SELECT` or `READ` privilege on `v$parameter` or `v$paramater2` fixed tables, or if you want to parse the warning string yourself and then modify and set the new value using `SET_WARNING_SETTING_STRING`.

#### 192.2.7 SET_WARNING_SETTING_STRING Procedure

This procedure replaces previous settings with the new value.

The warning string may contain mix of category and warning numbers using the same syntax as used on the right hand side of '=' when issuing an `ALTER SESSION` or `SYSTEM SET PLSQL_WARNINGS` command. This will have same effect as `ALTER SESSION` or `ALTER SYSTEM` command.

##### Syntax

    DBMS_WARNING.SET_WARNING_SETTING_STRING (
       warning_value   IN   VARCHAR2,
       scope           IN   VARCHAR2);

##### Parameters

Table 192-7 SET_WARNING_SETTING_STRING Procedure Parameters

| Parameter       | Description                                                                                                                          |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `warning_value` | The new string that will constitute the new value.                                                                                   |
| `scope`         | This will specify if the changes are being done in the session context, or system context. Allowed values are `SESSION` or `SYSTEM`. |
