## 232  OWA_SEC

The `OWA_SEC` package provides an interface for custom authentication.

**See Also:**

For more information about implementation of this package:

- [Oracle Fusion Middleware Administrator's Guide for Oracle HTTP Server](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=HSADM)

- [Oracle Fusion Middleware User's Guide for mod_plsql](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=YPMOD)

The chapter contains the following topics:

- Operational Notes

- Summary of OWA_SEC Subprograms

### 232.1 OWA_SEC Operational Notes

Parameters that have default values are optional.

### 232.2 Summary of OWA_SEC Subprograms

This table lists the OWA_SEC subprograms in alphabetical order and briefly describes them.

Table 232-1 OWA_SEC Package Subprograms

| Subprogram                     | Description                                                 |
|:-------------------------------|:------------------------------------------------------------|
| GET_CLIENT_HOSTNAME Function   | Returns the client's hostname                               |
| GET_CLIENT_IP Function         | Returns the client's IP address                             |
| GET_PASSWORD Function          | Returns the password that the user entered                  |
| GET_USER_ID Function           | Returns the username that the user entered                  |
| SET_AUTHORIZATION Procedure    | Enables the PL/SQL application to use custom authentication |
| SET_PROTECTION_REALM Procedure | Defines the realm that the page is in                       |

#### 232.2.1 GET_CLIENT_HOSTNAME Function

This function returns the hostname of the client.

##### Syntax

    OWA_SEC.GET_CLIENT_HOSTNAME
     RETURN VARCHAR2;

##### Return Values

The hostname.

#### 232.2.2 GET_CLIENT_IP Function

This function returns the IP address of the client.

##### Syntax

    OWA_SEC.GET_CLIENT_IP
      RETURN OWA_UTIL.IP_ADDRESS;

##### Return Values

The IP address. The `owa_util.ip_address datatype` is a PL/SQL table where the first four elements contain the four numbers of the IP address. For example, if the IP address is `123.45.67.89` and the variable `ipaddr` is of the owa_util.ip_address datatype, the variable would contain the following values:

    ipaddr(1) = 123
    ipaddr(2) = 45
    ipaddr(3) = 67
    ipaddr(4) = 89

#### 232.2.3 GET_PASSWORD Function

This function returns the password that the user used to log in.

##### Syntax

    OWA_SEC.GET_PASSWORD
      RETURN VARCHAR2;

##### Return Values

The password.

##### Usage Notes

For security reasons, this function returns a true value only when custom authentication is used. If you call this function when you are not using custom authentication, the function returns an undefined value. Thus, the database passwords are not exposed.

#### 232.2.4 GET_USER_ID Function

This function returns the username that the user used to log in.

##### Syntax

    OWA_SEC.GET_USER_ID
      RETURN VARCHAR2;

##### Return Values

The username.

#### 232.2.5 SET_AUTHORIZATION Procedure

This procedure, called in the initialization portion of the OWA_CUSTOM package, sets the authorization scheme for the PL/SQL Gateway.

This implements your `authorize` function, which authorizes the user before his requested procedure is run. The placement of the `authorize` function depends on the scheme you select.

##### Syntax

    OWA_SEC.SET_AUTHORIZATION(
        scheme         IN       INTEGER);

##### Parameters

Table 232-2 SET_AUTHORIZATION Procedure Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `scheme`  | The authorization scheme. It is one of the following schemes for `SET_AUTHORIZATION`:<br>• `OWA_SEC.NO_CHECK` - Specifies that the PL/SQL application is not to do any custom authentication. This is the default.<br>• `OWA_SEC.GLOBAL` - Defines an authorize function that is called for all users and all procedures. This is the `OWA_CUSTOM`.[AUTHORIZE Function](OWA_CUSTOM.md) in the "`sys`" schema.<br>• `OWA_SEC.PER_PACKAGE `- Define an `authorize` function that is called when procedures in a package or anonymous procedures are called. If the procedures are in a package, the package.`AUTHORIZE` function in the user's schema is called to authorize the user. If the procedures are not in a package, then the anonymous `authorize` function in the user's schema is called.<br>• `OWA_SEC.CUSTOM` - Implements different authorize functions for each user. The function `OWA_CUSTOM`.[AUTHORIZE Function](OWA_CUSTOM.md) in the user's schema is called to authorize the user. If the user's schema does not contain an `OWA_CUSTOM`.AUTHORIZE Function, the PL/SQL Gateway looks for it in the "sys" schema.<br>• The custom `authorize` function has the following signature:<br>`FUNCTION AUTHORIZE `<br>`  RETURN BOOLEAN;`<br>If the function returns `TRUE`, authentication succeeded. If it returns `FALSE`, authentication failed. If the `authorize` function is not defined, the Gateway returns an error and fails. |

**Related Topics**

- [OWA_CUSTOM](OWA_CUSTOM.md)

#### 232.2.6 SET_PROTECTION_REALM Procedure

This procedure sets the realm of the page that is returned to the user. The user enters a username and login that already exist in the realm.

##### Syntax

    OWA_SEC.SET_PROTECTION_REALM(
       realm      IN      VARCHAR2);

##### Parameters

Table 232-3 SET_PROTECTION_REALM Procedure Parameters

| Parameter | Description                                                             |
|:----------|:------------------------------------------------------------------------|
| `realm`   | The realm where the page belongs. This string is displayed to the user. |
