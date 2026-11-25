## 227  OWA_COOKIE

The OWA_COOKIE package provides an interface for sending and retrieving HTTP cookies from the client's browser.

**See Also:**

For more information about implementation of this package:

- [Oracle Fusion Middleware Administrator's Guide for Oracle HTTP Server](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=HSADM)

- [Oracle Fusion Middleware User's Guide for mod_plsql](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=YPMOD)

The chapter contains the following topics:

- Overview

- Types

- Rules and Limits

- Summary of OWA_COOKIE Subprograms

### 227.1  OWA_CUSTOM Overview

Cookies are opaque strings sent to the browser to maintain state between HTTP calls. State can be maintained throughout the client's sessions, or longer if an expiration date is included. The system date is calculated with reference to the information specified in the OWA_CUSTOM package.

### 227.2 OWA_COOKIE Types

This datatype contains cookie name-value pairs.

Since the HTTP standard allows cookie names to be overloaded (that is, multiple values can be associated with the same cookie name), there is a PL/SQL `RECORD` holding all values associated with a given cookie name.

    TYPE vc_arr IS TABLE OF VARCHAR2(4000) INDEX BY BINARY_INTEGER.

    TYPE COOKIE IS RECORD (
       name           VARCHAR2(4000),
       vals           vc_arr,
       num_vals       INTEGER);

### 227.3 OWA_COOKIE Rules and Limits

All HTTP headers must be in English and the ASCII character set. If the headers are generated from the database, verify they are created in the English language.

### 227.4 Summary of OWA_COOKIE Subprograms

This table lists the `OWA_COOKIE` subprograms and briefly describes them.

Table 227-1 OWA_COOKIE Package Subprograms

| Subprogram        | Description                                      |
|:------------------|:-------------------------------------------------|
| GET Function      | Gets the value of the specified cookie           |
| GET_ALL Procedure | Gets all cookie name-value pairs                 |
| REMOVE Procedure  | Removes the specified cookie                     |
| SEND procedure    | Generates a "Set-Cookie" line in the HTTP header |

#### 227.4.1 GET Function

This function returns the values associated with the specified cookie. The values are returned in a `OWA_COOKIE.COOKIE DATA TYPE` .

##### Syntax

    OWA_COOKIE.GET(
        name           IN       VARCHAR2)
      RETURN COOKIE;

##### Parameters

Table 227-2 GET Function Parameters

| Parameter | Description             |
|:----------|:------------------------|
| `name`    | The name of the cookie. |

##### Return Values

`OWA_COOKIE.COOKIE` `DATA` `TYPE`.

#### 227.4.2 GET_ALL Procedure

This procedure returns all cookie names and their values from the client's browser. The values appear in the order in which they were sent from the browser.

##### Syntax

    OWA_COOKIE.GET_ALL(
       names          OUT      vc_arr,
       vals           OUT      vc_arr,
       num_vals       OUT      INTEGER);

##### Parameters

Table 227-3 GET_ALL Procedure Parameters

| Parameter  | Description                       |
|:-----------|:----------------------------------|
| `names`    | The names of the cookies.         |
| `vals`     | The values of the cookies.        |
| `num_vals` | The number of cookie-value pairs. |

#### 227.4.3 REMOVE Procedure

This procedure forces a cookie to expire immediately by setting the "expires" field of a Set-Cookie line in the HTTP header to "01-Jan-1990".

This procedure must be called within the context of an HTTP header.

##### Syntax

    OWA_COOKIE.REMOVE(
       name           IN       VARCHAR2,
       val            IN       VARCHAR2,
       path           IN       VARCHAR2   DEFAULT NULL);

##### Parameters

Table 227-4 REMOVE Procedure Parameters

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | The name of the cookie to expire. |
| `val`     | The value of the cookie.          |
| `path`    | \[Currently unused\]              |

#### 227.4.4 SEND procedure

This procedure generates a Set-Cookie line, which transmits a cookie to the client.

This procedure must occur in the context of an HTTP header.

##### Syntax

    OWA_COOKIE.SEND(
       name           in       varchar2,
       value          in       varchar2,
       expires        in       date       DEFAULT NULL,
       path           in       varchar2   DEFAULT NULL,
       domain         in       varchar2   DEFAULT NULL,
       secure         in       varchar2   DEFAULT NULL);

##### Parameters

Table 227-5 SEND Procedure Parameters

| Parameter | Description                                                                            |
|:----------|:---------------------------------------------------------------------------------------|
| `name`    | The name of the cookie.                                                                |
| `value`   | The value of the cookie.                                                               |
| `expires` | The date at which the cookie will expire                                               |
| `path`    | The value for the path field.                                                          |
| `domain`  | The value for the domain field.                                                        |
| `secure`  | If the value of this parameter is not `NULL`, the "secure" field is added to the line. |
