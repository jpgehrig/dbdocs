## 229  OWA_IMAGE

The `OWA_IMAGE` package provides an interface to access the coordinates where a user clicked on an image.

The chapter contains the following topics:

- Overview

- Types

- Variables

- Examples

- Summary of OWA_IMAGE Subprograms

**See Also:**

For more information about implementation of this package:

- [Oracle Fusion Middleware Administrator's Guide for Oracle HTTP Server](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=HSADM)

- [Oracle Fusion Middleware User's Guide for mod_plsql](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=YPMOD)

### 229.1 OWA_IMAGE Overview

Use this package when you have any image map whose destination links invoke the PL/SQL Gateway.

### 229.2 OWA_IMAGE Types

This datatype (`point`) contain the `X` and `Y` values of a coordinate, and so provides the coordinates of a user's click on an imagemap.

It is defined as:

    TYPE POINT IS TABLE OF VARCHAR2(32767) INDEX BY BINARY_INTEGER

### 229.3 OWA_IMAGE Variables

This package variable (`null_point`) of `TYPE` `POINT` is used to default point parameters. Both the X and the Y fields of this variable are `NULL`.

### 229.4 OWA_IMAGE Examples

This example shows use of `OWA_IMAGE`.

    CREATE OR REPLACE PROCEDURE process_image
        (my_img in OWA_IMAGE.POINT)
        AS
        x integer := OWA_IMAGE.GET_X(my_img);
        y integer := OWA_IMAGE.GET_Y(my_img);
    BEGIN
        /* process the coordinate */
    END

### 229.5 Summary of OWA_IMAGE Subprograms

This table lists the OWA_IMAGE subprograms and briefly describes them.

Table 229-1 OWA_IMAGE Package Subprograms

| Subprogram     | Description                      |
|:---------------|:---------------------------------|
| GET_X Function | Gets the X value of a point type |
| GET_Y Function | Gets the Y value of a point type |

#### 229.5.1 GET_X Function

This function returns the `X` coordinate of the point where the user clicked on an image map.

##### Syntax

    OWA_IMAGE.GET_X(
       p        IN        point)
     RETURN INTEGER;

##### Parameters

Table 229-2 GET_X Function Parameters

| Parameter | Description                       |
|:----------|:----------------------------------|
| `p`       | The point where the user clicked. |

##### Return Values

The X coordinate as an integer.

#### 229.5.2 GET_Y Function

This function returns the Y coordinate of the point where the user clicked on an image map.

##### Syntax

    OWA_IMAGE.GET_Y(
       p        IN        point)
     RETURN INTEGER;

##### Parameters

Table 229-3 GET_Y Function Parameters

| Parameter | Description                       |
|:----------|:----------------------------------|
| `p`       | The point where the user clicked. |

##### Return Values

The Y coordinate as an integer.
