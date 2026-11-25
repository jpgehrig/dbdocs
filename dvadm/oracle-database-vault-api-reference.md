Oracle Database Vault provides a rich set of APIs, both in PL/SQL packages and in standalone procedures.

- DBMS_MACADM PL/SQL Package Contents
  The `DBMS_MACADM` package enables you to configure the realms, factors, rule sets, command rules, secure application roles, and Oracle Label Security policies.
- DBMS_MACSEC_ROLES PL/SQL Package Contents
  The `DBMS_MACSEC_ROLES` package enables you to check and set Oracle Database Vault secure application roles.
- DBMS_MACUTL PL/SQL Package Contents
  The `DBMS_MACUTL` PL/SQL package defines constants and utility methods that are commonly used by other Oracle Database Vault packages, such as error handling.
- CONFIGURE_DV PL/SQL Procedure
  The `CONFIGURE_DV` configures the initial two Oracle Database user accounts, which are granted the `DV_OWNER` and `DV_ACCTMGR` roles, respectively.
- DVF PL/SQL Interface Contents
  The `DVF` schema provides a set of factor-related PL/SQL functions.

### 23.1 DBMS_MACADM PL/SQL Package Contents

The `DBMS_MACADM` package enables you to configure the realms, factors, rule sets, command rules, secure application roles, and Oracle Label Security policies.

The `DBMS_MACADM` package is available only for users who have been granted the `DV_ADMIN` or `DV_OWNER` role.

#### DBMS_MACADM Realm Procedures

Table 23-1 lists the realm procedures in the `DBMS_MACADM` package.

Table 23-1 DBMS_MACADM Realm Procedures

| Procedure                            | Description                                                                                                                                     |
|:-------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `ADD_AUTH_TO_REALM` procedure        | Authorizes a user or role to access a realm as an owner or a participant                                                                        |
| `ADD_OBJECT_TO_REALM` procedure      | Registers a set of objects for realm protection                                                                                                 |
| `CREATE_REALM` procedure             | Creates a realm                                                                                                                                 |
| `DELETE_AUTH_FROM_REALM` procedure   | Removes the authorization of a user or role to access a realm                                                                                   |
| `DELETE_OBJECT_FROM_REALM` procedure | Removes a set of objects from realm protection                                                                                                  |
| `DELETE_REALM` procedure             | Deletes a realm, including its related Database Vault configuration information that specifies who is authorized and what objects are protected |
| `DELETE_REALM_CASCADE` procedure     | Deletes a realm, including its related Database Vault configuration information that specifies who is authorized and what objects are protected |
| `RENAME_REALM` procedure             | Renames a realm. The name change takes effect everywhere the realm is used.                                                                     |
| `UPDATE_REALM` procedure             | Updates a realm                                                                                                                                 |
| `UPDATE_REALM_AUTH` procedure        | Updates the authorization of a user or role to access a realm                                                                                   |

#### DBMS_MACADM Rule Set and Rule Procedures

Table 23-2 lists the rule set and rule procedures in the `DBMS_MACADM` package.

Table 23-2 DBMS_MACADM Rule Set and Rule Procedures

| Procedure                             | Description                                                                       |
|:--------------------------------------|:----------------------------------------------------------------------------------|
| `CREATE_RULE_SET` procedure           | Creates a rule set                                                                |
| `RENAME_RULE_SET` procedure           | Renames a rule set. The name change takes effect everywhere the rule set is used. |
| `DELETE_RULE_FROM_RULE_SET` procedure | Deletes a rule from a rule set                                                    |
| `DELETE_RULE_SET` procedure           | Deletes a rule set                                                                |
| `UPDATE_RULE_SET` procedure           | Updates a rule set                                                                |
| `CREATE_RULE` procedure               | Creates a rule                                                                    |
| `ADD_RULE_TO_RULE_SET` procedure      | Adds a rule to a rule set                                                         |
| `DELETE_RULE` procedure               | Deletes a rule                                                                    |
| `RENAME_RULE` procedure               | Renames a rule. The name change takes effect everywhere the rule is used.         |
| `UPDATE_RULE` procedure               | Updates a rule                                                                    |

#### DBMS_MACADM Command Rule Procedures

Table 23-3 lists the command rule procedures in the `DBMS_MACADM` package.

Table 23-3 DBMS_MACADM Command Rule Procedures

| Procedure                                 | Description                                                                                                                   |
|:------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| `CREATE_COMMAND_RULE` procedure           | Creates a command rule, associates it with a rule set, and lets you enable the command rule for rule checking with a rule set |
| `CREATE_CONNECT_COMMAND_RULE` procedure   | Creates a CONNECT command rule                                                                                                |
| `CREATE_SESSION_EVENT_CMD_RULE` procedure | Creates a session event command rule, using the ALTER SESSION SQL statement                                                   |
| `CREATE_SYSTEM_EVENT_CMD_RULE` procedure  | Creates a system event command rule, using the ALTER SYSTEM SQL statement                                                     |
| `DELETE_COMMAND_RULE` procedure           | Drops a command rule declaration                                                                                              |
| `DELETE_CONNECT_COMMAND_RULE` procedure   | Drops a CONNECT command rule declaration                                                                                      |
| `DELETE_SESSION_EVENT_CMD_RULE` procedure | Drops a SESSION_EVENT_CMD command rule declaration                                                                            |
| `DELETE_SYSTEM_EVENT_CMD_RULE` procedure  | Drops a SYSTEM_EVENT_CMD command rule declaration                                                                             |
| `UPDATE_COMMAND_RULE` procedure           | Updates a command rule declaration                                                                                            |
| `UPDATE_CONNECT_COMMAND_RULE` procedure   | Updates a CONNECT command rule declaration                                                                                    |
| `UPDATE_SESSION_EVENT_CMD_RULE` procedure | Updates a SESSION_EVENT_CMD command rule declaration                                                                          |
| `UPDATE_SYSTEM_EVENT_CMD_RULE` procedure  | Updates a SYSTEM_EVENT_CMD command rule declaration                                                                           |

#### DBMS_MACADM Factor Procedures and Functions

lists the factor procedures and functions in the `DBMS_MACADM` package.

Table 23-4 DBMS_MACADM Factor Procedures and Functions

| Procedure or Function              | Description                                                                                                                                                      |
|:-----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ADD_FACTOR_LINK` procedure        | Specifies a parent-child relationship for two factors                                                                                                            |
| `ADD_POLICY_FACTOR` procedure      | Specifies that the label for a factor contributes to the Oracle Label Security label for a policy.                                                               |
| `CHANGE_IDENTITY_FACTOR` procedure | Associates an identity with a different factor                                                                                                                   |
| `CHANGE_IDENTITY_VALUE` procedure  | Updates the value of an identity                                                                                                                                 |
| `CREATE_DOMAIN_IDENTITY` procedure | Adds an Oracle Real Application Clusters (Oracle RAC) database node to the domain factor identities and labels it according to the Oracle Label Security policy. |
| `CREATE_FACTOR` procedure          | Creates a factor                                                                                                                                                 |
| `CREATE_FACTOR_TYPE` procedure     | Creates a factor type                                                                                                                                            |
| `CREATE_IDENTITY` procedure        | Creates an identity                                                                                                                                              |
| `CREATE_IDENTITY_MAP` procedure    | Defines a set of tests that are used to derive the identity of a factor from the value of linked child factors (subfactors)                                      |
| `DELETE_FACTOR` procedure          | Deletes a factor                                                                                                                                                 |
| `DELETE_FACTOR_LINK` procedure     | Removes a parent-child relationship for two factors                                                                                                              |
| `DELETE_FACTOR_TYPE` procedure     | Deletes a factor type                                                                                                                                            |
| `DELETE_IDENTITY` procedure        | Removes an identity                                                                                                                                              |
| `DELETE_IDENTITY_MAP` procedure    | Removes an identity map from a factor                                                                                                                            |
| `DROP_DOMAIN_IDENTITY` procedure   | Removes an Oracle RAC database node from a domain                                                                                                                |
| `GET_INSTANCE_INFO` function       | Returns information from the `SYS.V_$INSTANCE` system table about the current database instance; returns a `VARCHAR2` value                                      |
| `GET_SESSION_INFO` function        | Returns information from the `SYS.V_$SESSION` system table for the current session; returns a `VARCHAR2` value                                                   |
| `RENAME_FACTOR` procedure          | Renames a factor. The name change takes effect everywhere the factor is used.                                                                                    |
| `RENAME_FACTOR_TYPE` procedure     | Renames a factor type. The name change takes effect everywhere the factor type is used.                                                                          |
| `UPDATE_FACTOR` procedure          | Updates a factor                                                                                                                                                 |
| `UPDATE_FACTOR_TYPE` procedure     | Updates the description of a factor type                                                                                                                         |
| `UPDATE_IDENTITY` procedure        | Updates the trust level of a factor identity                                                                                                                     |

#### DBMS_MACADM Secure Application Role Procedures

Table 23-5 lists the secure application role procedures in the `DBMS_MACADM` package.

Table 23-5 DBMS_MACADM Secure Application Role Procedures

| Procedure                 | Description                                                                                                         |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------|
| `CREATE_ROLE` procedure   | Creates an Oracle Database Vault secure application role                                                            |
| `DELETE_ROLE` procedure   | Deletes an Oracle Database Vault secure application role                                                            |
| `RENAME_ROLE` procedure   | Renames an Oracle Database Vault secure application role. The name change takes effect everywhere the role is used. |
| `UNASSIGN_ROLE` procedure | Unassigns an Oracle Database Vault secure application role from a user                                              |
| `UPDATE_ROLE` procedure   | Updates a Oracle Database Vault secure application role                                                             |

#### DBMS_MACADM Oracle Label Security Procedures

Table 23-6 lists the Oracle Label Security procedures in the `DBMS_MACADM` package.

Table 23-6 DBMS_MACADM Oracle Label Security Procedures

| Procedure                             | Description                                                                                                                            |
|:--------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `CREATE_MAC_POLICY` procedure         | Specifies the algorithm that is used to merge labels when computing the label for a factor, or the Oracle Label Security Session label |
| `CREATE_POLICY_LABEL` procedure       | Labels an identity within an Oracle Label Security policy                                                                              |
| `DELETE_MAC_POLICY_CASCADE` procedure | Deletes all Oracle Database Vault objects related to an Oracle Label Security policy.                                                  |
| `DELETE_POLICY_FACTOR` procedure      | Removes the factor from contributing to the Oracle Label Security label                                                                |
| `DELETE_POLICY_LABEL` procedure       | Removes the label from an identity within an Oracle Label Security policy                                                              |
| `UPDATE_MAC_POLICY` procedure         | Specifies the algorithm that is used to merge labels when computing the label for a factor, or the Oracle Label Security Session label |

#### DBMS_MACADM Database Vault Policy Procedures

Table 23-7 lists the Database Vault policy procedures in the `DBMS_MACADM` package.

Table 23-7 DBMS_MACADM Database Vault Policy Procedures

| Procedure                               | Description                                                  |
|:----------------------------------------|:-------------------------------------------------------------|
| `ADD_CMD_RULE_TO_POLICY` procedure      | Adds a command rule to a Database Vault policy               |
| `ADD_OWNER_TO_POLICY` procedure         | Adds an owner to a Database Vault policy                     |
| `ADD_REALM_TO_POLICY` procedure         | Adds a realm to a Database Vault policy                      |
| `CREATE_POLICY` procedure               | Creates a Database Vault policy                              |
| `DELETE_CMD_RULE_FROM_POLICY` procedure | Deletes a command rule from a Database Vault policy          |
| `DELETE_OWNER_FROM_POLICY` procedure    | Deletes an owner from a Database Vault policy                |
| `DELETE_REALM_FROM_POLICY` procedure    | Deletes a realm from a Database Vault policy                 |
| `DROP_POLICY` procedure                 | Drops a Database Vault policy                                |
| `RENAME_POLICY` procedure               | Renames a Database Vault policy                              |
| `UPDATE_POLICY_DESCRIPTION` procedure   | Updates a Database Vault policy description                  |
| `UPDATE_POLICY_STATE` procedure         | Updates the enablement status of the a Database Vault policy |

#### DBMS_MACADM General Administrative Procedures

Table 23-8 lists the general administrative procedures in the `DBMS_MACADM` package.

Table 23-8 DBMS_MACADM General Administrative Procedures

| Procedure                                | Description                                                                                                                                                                                 |
|:-----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ADD_NLS_DATA` procedure                 | Adds a new language to Oracle Database Vault                                                                                                                                                |
| `ADD_APP_EXCEPTION procedure`            | Enables a common user or package to access local schemas                                                                                                                                    |
| `AUTHORIZE_DATAPUMP_USER` procedure      | Authorizes a user to perform Oracle Data Pump operations when Oracle Database Vault is enabled                                                                                              |
| `AUTHORIZE_DDL` procedure                | Grants a user authorization to execute data definition language (DDL) statements                                                                                                            |
| `AUTHORIZE_MAINTENANCE_USER` procedure   | Grants a user authorization to perform Information Lifecycle Management (ILM) operations                                                                                                    |
| `AUTHORIZE_PROXY_USER` procedure         | Grants a proxy user authorization to proxy other user accounts                                                                                                                              |
| `AUTHORIZE_SCHEDULER_USER` procedure     | Authorizes a user to schedule database jobs when Oracle Database Vault is enabled                                                                                                           |
| `AUTHORIZE_TTS_USER` procedure           | Authorizes a user to perform Oracle Data Pump transportable tablespace operations for a tablespace when Oracle Database Vault is enabled                                                    |
| `DELETE_APP_EXCEPTION` procedure         | Deletes the exception for a common user or package to access a local schema                                                                                                                 |
| `DISABLE_DV_DICTIONARY_ACCTS` procedure  | Prevents users from logging into the `DVSYS` and `DFV` schema accounts                                                                                                                      |
| `DISABLE_DV_PATCH_ADMIN`                 | Disables auditing of the `DV_PATCH_ADMIN` user                                                                                                                                              |
| `DISABLE_DV` procedure                   | Disables Oracle Database Vault                                                                                                                                                              |
| `DISABLE_APP_PROTECTION procedure`       | Disables Database Vault operation control                                                                                                                                                   |
| `DISABLE_ORADEBUG` procedure             | Disables the use of the `ORADEBUG` utility in an Oracle Database Vault environment                                                                                                          |
| `ENABLE_DV_DICTIONARY_ACCTS` procedure   | Enables users to log into the `DVSYS` and `DFV` schema accounts                                                                                                                             |
| `ENABLE_DV_PATCH_ADMIN`                  | Enables auditing of the `DV_PATCH_ADMIN` user                                                                                                                                               |
| `ENABLE_DV` procedure                    | Enables Oracle Database Vault                                                                                                                                                               |
| `ENABLE_APP_PROTECTION` procedure        | Enables Database Vault operations control                                                                                                                                                   |
| `ENABLE_ORADEBUG` procedure              | Enables the use of the `ORADEBUG` utility in an Oracle Database Vault environment                                                                                                           |
| `UNAUTHORIZE_DATAPUMP_USER` procedure    | Revokes the authorization that was granted by the `DBMS_MACADM.AUTHORIZE_DATAPUMP_USER` procedure                                                                                           |
| `UNAUTHORIZE_DDL` procedure              | Revokes authorization from a user who was granted authorization to execute DDL statements through the `DBMS_MACDM.AUTHORIZE_DDL` procedure                                                  |
| `UNAUTHORIZE_MAINTENANCE_USER` procedure | Revokes authorization to perform ILM operations                                                                                                                                             |
| `UNAUTHORIZE_PROXY_USER` procedure       | Revokes authorization from a user who was granted proxy authorization from the `DBMS_MACADM.AUTHORIZE_PROXY_USER` procedure                                                                 |
| `UNAUTHORIZE_SCHEDULER_USER` procedure   | Revokes authorization that was granted by the `DBMS_MACADM.AUTHORIZE_SCHEDULER_USER` procedure                                                                                              |
| `UNAUTHORIZE_TTS_USER` procedure         | Revokes from authorization a user who had been granted authorization to perform Oracle Data Pump transportable tablespace operations for a tablespace when Oracle Database Vault is enabled |

**Parent topic:** Oracle Database Vault API Reference

### 23.2 DBMS_MACSEC_ROLES PL/SQL Package Contents

The `DBMS_MACSEC_ROLES` package enables you to check and set Oracle Database Vault secure application roles.

This package is available to the general database account population.

Table 23-9 lists the contents of the `DBMS_MACSEC_ROLES` package.

Table 23-9 DBMS_MACSEC_ROLES PL/SQL Package Contents

| Procedure or Function   | Description                                                                                                                                              |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CAN_SET_ROLE` function | Checks whether the user invoking the method is authorized to use the specified Oracle Database Vault secure application role. Returns a `BOOLEAN` value. |
| `SET_ROLE` procedure    | Issues the `SET ROLE` statement for an Oracle Database Vault secure application role.                                                                    |

**Parent topic:** Oracle Database Vault API Reference

### 23.3 DBMS_MACUTL PL/SQL Package Contents

The `DBMS_MACUTL` PL/SQL package defines constants and utility methods that are commonly used by other Oracle Database Vault packages, such as error handling.

This package can be run by the general database account population. This allows for security developers to leverage the constants in scripted configuration files. Utility methods such as `USER_HAS_ROLE` can also be used in Oracle Database Vault rules.

Table 23-10 lists the `DBMS_MACUTL` package contents.

Table 23-10 DBMS_MACUTL PL/SQL Package Contents

| Procedure or Function                | Description                                                                                                    |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------|
| `CHECK_DVSYS_DML_ALLOWED` procedure  | Verifies that public-packages are not being bypassed by users updating the Oracle Database Vault configuration |
| `GET_CODE_VALUE` function            | Looks up the value for a code within a code group.                                                             |
| `GET_SECOND` function                | Returns the seconds in Oracle SS format (00-59). Useful for rule expressions based on time data                |
| `GET_MINUTE` function                | Returns the minute in Oracle MI format (00–59). Useful for rule expressions based on time data                 |
| `GET_HOUR` function                  | Returns the month in Oracle HH24 format (00–23). Useful for rule expressions based on time data                |
| `GET_DAY` function                   | Returns the day in Oracle DD format (01–31). Useful for rule expressions based on time data                    |
| `GET_MONTH` function                 | Returns the month in Oracle MM format (01–12). Useful for rule expressions based on time data                  |
| `GET_YEAR` function                  | Returns the year in Oracle YYYY format (0001–9999). Useful for rule expressions based on time data             |
| `IS_ALPHA` function                  | Checks whether the character is alphabetic                                                                     |
| `IS_DIGIT` function                  | Checks whether the character is numeric                                                                        |
| `IS_DVSYS_OWNER` function            | Determines whether a user is authorized to manage the Oracle Database Vault configuration                      |
| `IS_OLS_INSTALLED` function          | Returns an indicator regarding whether Oracle Label Security is installed                                      |
| `IS_OLS_INSTALLED_VARCHAR` function  | Returns an indicator regarding whether Oracle Label Security is installed                                      |
| `USER_HAS_ROLE` function             | Checks whether a user has a role privilege, directly or indirectly (through another role)                      |
| `USER_HAS_ROLE_VARCHAR` function     | Checks whether a user has a role privilege, directly or indirectly (through another role)                      |
| `USER_HAS_SYSTEM_PRIVILEGE` function | Checks whether a user has a system privilege, directly or indirectly (through a role)                          |

**Parent topic:** Oracle Database Vault API Reference

### 23.4 CONFIGURE_DV PL/SQL Procedure

The `CONFIGURE_DV` configures the initial two Oracle Database user accounts, which are granted the `DV_OWNER` and `DV_ACCTMGR` roles, respectively.

This procedure is used as part of the registration process for Oracle Database Vault with an Oracle database. You only need to use it once for the database instance.

**Parent topic:** Oracle Database Vault API Reference

### 23.5 DVF PL/SQL Interface Contents

The `DVF` schema provides a set of factor-related PL/SQL functions.

The functions are then available to the general database account population through PL/SQL functions and standard SQL.

Table 23-11 lists the `DVF` factor functions.

Table 23-11 DVF PL/SQL Interface Contents

| Function                      | Description                                                                                                                                                                                                                   |
|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `F$CLIENT_IP`                 | Returns the IP address of the computer from which the client is connected                                                                                                                                                     |
| `F$DATABASE_DOMAIN`           | Returns the domain of the database as specified in the `DB_DOMAIN` initialization parameter                                                                                                                                   |
| `F$DATABASE_HOSTNAME`         | Returns the host name of the computer on which the database instance is running                                                                                                                                               |
| `F$DATABASE_INSTANCE`         | Returns the database instance identification number of the current database instance                                                                                                                                          |
| `F$DATABASE_IP`               | Returns the IP address of the computer on which the database instance is running                                                                                                                                              |
| `F$DATABASE_NAME`             | Returns the name of the database as specified in the `DB_NAME` initialization parameter                                                                                                                                       |
| `F$DOMAIN`                    | Returns a named collection of physical, configuration, or implementation-specific factors in the run-time environment (for example, a networked IT environment or subset of it) that operates at a specific sensitivity level |
| `F$ENTERPRISE_IDENTITY`       | Returns the enterprise-wide identity for a user                                                                                                                                                                               |
| `F$IDENTIFICATION_TYPE`       | Returns the way the schema of a user was created in the database. Specifically, it reflects the `IDENTIFIED` clause in the `CREATE USER` or `ALTER USER` syntax.                                                              |
| `F$LANG`                      | Returns the ISO abbreviation for the language name, a shorter form than the existing `LANGUAGE` parameter                                                                                                                     |
| `F$LANGUAGE`                  | Returns the language and territory currently used by your session, in `VARCHAR2` data type, along with the database character set                                                                                             |
| `F$MACHINE`                   | Returns the computer (host) name for the database client that established the database session.                                                                                                                               |
| `F$NETWORK_PROTOCOL`          | Returns the network protocol being used for communication, as specified in the `PROTOCOL`=`protocol` portion of the connect string                                                                                            |
| `F$PROXY_ENTERPRISE_IDENTITY` | Returns the Oracle Internet Directory distinguished name (DN) when the proxy user is an enterprise user                                                                                                                       |
| `F$SESSION_USER`              | Returns the database user name by which the current user is authenticated                                                                                                                                                     |

**Parent topic:** Oracle Database Vault API Reference
