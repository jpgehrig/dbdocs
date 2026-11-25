The following topics contain information that is specific to this release of Oracle Database Gateway for WebSphere MQ:

### Changes and Enhancements

These topics describe the changes and enhancements included in this release.

#### Oracle Database Dependencies

This topic explains Oracle database dependencies.

This release of Oracle Database Gateway for WebSphere MQ requires the latest released patch set for Oracle Database 12c Release 2 (12.2), or for the Oracle database release that you are using.

#### Support for Large Data Buffers

The PL/SQL RAW data type limitation is 32 KB (32767) bytes.

For large loads, you must use the TABLE OF RAWS data type. For more information about support for large data buffers, refer to:

**Related Topics**

- [The PGM, PGM_UTL8, and PGM_SUP Packages](database-gateway-webspheremq-pgm-packages.md)

#### DG4MQ Data Types

This table provides information about Oracle Database Gateway for WebSphere MQ (DG4MQ) data types.

| Data Type  | V401               | V804           | V817 and V901   | Oracle10g Release 2 and higher |
|:-----------|:-------------------|:---------------|:----------------|:-------------------------------|
| `MQOD`     | `PGM.MQOD@dblink`  | `PGM.MQOD`     | `PGM.MQOD`      | `PGM.MQOD`                     |
| `MQMD`     | `PGM.MQMD@dblink`  | `PGM.MQMD`     | `PGM.MQMD`      | `PGM.MQMD`                     |
| `MQPMO`    | `PGM.MQPMO@dblink` | `PGM.MQPMO`    | `PGM.MQPMO`     | `PGM.MQPMO`                    |
| `MQGMO`    | `PGM.MQGMO@dblink` | `PGM.MQGMO`    | `PGM.MQGMO`     | `PGM.MQGMO`                    |
| `MQODRAW`  | NA                 | `PGM.MQODRAW`  | `PGM8.MQODRAW`  | NA                             |
| `MQMDRAW`  | NA                 | `PGM.MQMDRAW`  | `PGM8.MQMDRAW`  | NA                             |
| `MQPMORAW` | NA                 | `PGM.MQPMORAW` | `PGM8.MQPMORAW` | NA                             |
| `MQGMORAW` | NA                 | `PGM.MQGMORAW` | `PGM8.MQGMORAW` | NA                             |

#### PGM_UTL Procedures

This table provides information about `PGM_UTL` procedures.

| Procedure      | V401 | V804                   | V817 and V901           | Oracle10g Release 2 and higher |
|:---------------|:-----|:-----------------------|:------------------------|:-------------------------------|
| `TO_RAW`       | NA   | `PGM_UTL.TO_RAW`       | `PGM_UTL8.TO_RAW `      | `PGM.TO_RAW`                   |
| `RAW_TO_MQMD`  | NA   | `PGM_UTL.RAW_TO_MQMD`  | `PGM_UTL8.RAW_TO_MQMD`  | `PGM.RAW_TO_MQMD`              |
| `RAW_TO_MQPMO` | NA   | `PGM_UTL.RAW_TO_MQPMO` | `PGM_UTL8.RAW_TO_MQPMO` | `PGM.RAW_TO_MQPMO`             |
| `RAW_TO_MQGMO` | NA   | `PGM_UTL.RAW_TO_MQGMO` | `PGM_UTL8.RAW_TO_MQGMO` | `PGM.RAW_TO_MQGMO`             |

**Note:**

For Oracle10g release 10.2.0, the `PGM.TO_RAW`, `PGM.RAW_TO_MQMD`, `PGM.RAW_TO_MQPMO` and `PGM.RAW_TO_MQGMO` procedures are added for backward compatibility.

#### DG4MQ API Prototype Changes

This table provides information about `DG4MQ` application programming interface changes.

| API       | V401 Arguments         | V804 Arguments      | V817 & V901 Arguments | 10g Release 2 and higher Arguments                                             |
|:----------|:-----------------------|:--------------------|:----------------------|:-------------------------------------------------------------------------------|
| `MQOPEN`  | `(MQOD,INT,INT)`       | `(RAW,INT,INT)`     | `(RAW,INT,INT)`       | `(PGM.MQOD,INT,INT)`                                                           |
| `MQPUT`   | `(INT,MQMD,MQPMO,RAW)` | `(INT,RAW,RAW,RAW)` | `(INT,RAW,RAW,RAW)`   | `(INT,PGM.MQMD,PGM_MQPMO,RAW) or (INT, PGM.MQMD, PGM_MQPMO, PGM.MQPUT_BUFFER)` |
| `MQGET`   | `(INT,MQMD,MQGMO,RAW)` | `(INT,RAW,RAW,RAW)` | `(INT,RAW,RAW,RAW)`   | `(INT,PGM.MQMD,PGM_MQGMO,RAW) or (INT, PGM.MQMD, PGM.MQGMO, PGM_MQGET_BUFFER)` |
| `MQCLOSE` | `(INT,INT)`            | `(INT,INT)`         | `(INT,INT)`           | `(INT,INT)`                                                                    |

**Related Topics**

- [The PGM, PGM_UTL8, and PGM_SUP Packages](database-gateway-webspheremq-pgm-packages.md)

#### DG4MQ Deployment Scripts

These DG4MQ deployment scripts are new in this release.

- `pgm.sql`

- `pgmobj.sql`

- `pgmdeploy.sql`

- `pgmundeploy.sql`

The gateway procedures in the PGM package are defined in `pgm.sql` and PGM_MQ\* data type definitions used by the procedures are defined in `pgmobj.sql`. For complete information about PGM package, DG4MQ gateway procedures and data type definitions, refer to:

**Related Topics**

- [The PGM, PGM_UTL8, and PGM_SUP Packages](database-gateway-webspheremq-pgm-packages.md)

#### Large Payload Support

DG4MQ 11g supports large payloads or messages longer than 32767 bytes.

For more information, refer to the `putlongsample.sql` and `getlongsample.sql` sample programs installed with the DG4MQ.

#### Database Link and Alias Library

A connection to the gateway is established through a database link.

From DG4MQ 10g release 2 and later, this database link is no longer associated with each DG4MQ gateway procedural call (for example, `PGM.MQPUT@dblink`). From 10g release 2 and later, it needs to be defined only once in the `MQOD` data type used by `MQOPEN`, and this database link is registered in the object handle returned by the `MQOPEN` call. Refer to the sample programs installed with the gateway for details. By default, a public database link, `dg4mqdepdblink`, is created with your default SID when DG4MQ deployment scripts are executed.

### Known Problems

This topic describes the known problems in this release.

The problems documented in this section are specific to the Oracle Database Gateway for WebSphere MQ and are known to exist in this release of the product. These problems will be fixed in a future gateway release. If you have any questions or concerns about these problems, contact Oracle Support Services.

A current list of problems is available online. Contact your local Oracle office for information about accessing this online information.

### Known Restrictions

This topic describes the known restrictions in this release.

The following restriction is known to exist for this release.

#### Customizing LOG_DESTINATION

There is a known issue when customizing the gateway initialization file for gateway tracing for Microsoft Windows platform. When customizing the path name of `LOG_DESTINATION`, the delimiter must be double backslashes. For example:

    LOG_DESTINATION=C:\\oracle\\product\\12.2\\dg4mqs\\dg4mq\\log\\dg4mqs.log

**Note:**

If `LOG_DESTINATION` is not defined for Microsoft Windows platform, a default name is used and the log is created in `ORACLE_HOME\dg4mq\trace` directory

#### Customizing deployment script pgmobj.sql

There is a known issue when customizing the gateway deployment script `pgmobj.sql` for Microsoft Windows platform. When defining the path name of `libdg4mq`, the delimiter must be backslashes. For example create or replace library `libdg4mq` as:

    CREATE OR REPLACE LIBRARY libdg4mq as 'C:\oracle\product\12.2\dg4mqs\bin\oradg4mqs.dll' transactional

or

    CREATE OR REPLACE LIBRARY libdg4mq as '$ORACLE_HOME\bin\oradg4mqs.dll' transactional

#### CALLBACK links

Oracle Database Gateway for WebSphere MQ does not support `CALLBACK` links. Trying a `CALLBACK` link with the gateway will return the following error message:

    ORA-02025: All tables in the SQL statement must be at the remote database
