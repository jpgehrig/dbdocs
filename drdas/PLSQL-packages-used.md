Oracle Database Provider for DRDA uses `DBMS_DRDAAS_ADMIN` and `DBMS_DRDAAS` PL/SQL packages and their APIs.

For in-depth information on the type map values used in these two packages, see [Datatype Support and Conversion in Oracle Database Provider for DRDA](datatype-support-and-conversion.md) .

### 13.1 DBMS_DRDAAS_ADMIN Package

`DBMS_DRDAAS_ADMIN` PL/SQL package grants DRDA package privileges to Oracle Database Provider for DRDA users. These privileges include the following:

- bind DRDA packages

- drop DRDA packages

- execute DRDA packages

- set package values

#### 13.1.1 DBMS_DRDAAS_ADMIN Privilege Constants

These constants are used with “`GRANT_PRIVILEGE`” and “`REVOKE_PRIVILEGE`”.

##### ALL_PRIVILEGE

This privilege grants all privileges to a client for an Application Package.

##### BIND_PRIVILEGE

This privilege allows a client to bind or rebind an Application Package to the database.

##### COPY_PRIVILEGE

This privilege allows a client to copy an existing Application Package to another name (optionally with different default package options).

##### EXECUTE_PRIVILEGE

This privilege allows a client to execute an existing Application Package.

##### DROP_PRIVILEGE

This privilege allows a client to drop an existing Application Package.

##### SET_PRIVILEGE

This privilege allows a client to set specific Application Package options. See the `SET_``XXX` functions elsewhere in this document.

**Related Topics**

- GRANT_PRIVILEGE
- REVOKE_PRIVILEGE

#### 13.1.2 GRANT_PRIVILEGE

Grants a privilege to the user for a DRDA package.

##### Syntax

    PROCEDURE grant_privilege(
       privilege_grant IN PLS_INTEGER,
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       user_name IN VARCHAR2);

##### Parameters

- `privilege_grant (IN) `

  Privilege to grant

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `user_name (IN)`

  Userid to grant privileges to

##### Usage Example

    begin
       dbms_drdaas_admin.grant_privilege ( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'ORACLE',
         'MYPACKAGE', 'DRDAUSR1' );
    end;

#### 13.1.3 REVOKE_PRIVILEGE

Revokes a privilege from a user for a DRDA package.

##### Syntax

    PROCEDURE revoke_privilege(
       privilege_revoke IN PLS_INTEGER,
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       user_name IN VARCHAR2);

##### Parameters

- `privilege_revoke (IN) `

  Privilege to revoke

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `user_name (IN)`

  Userid to revoke privileges from

##### Usage Example

    begin
       dbms_drdaas_admin.revoke_privilege ( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'ORACLE',
         'MYPACKAGE', 'DRDAUSR1' );
    end;

#### 13.1.4 DROP_PACKAGE

Drops all instances of a package by `package_name`.

##### Syntax

    procedure DROP_PACKAGE(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2 );

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

##### Usage Example

    begin
      dbms_drdaas_admin.drop_package(
        'ORACLE', 'MYPACKAGE' );
    end;

#### 13.1.5 DROP_PACKAGE_VN

Drops a package by `version_name`.

##### Syntax

    procedure DROP_PACKAGE_VN(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       version_name IN VARCHAR2 DEFAULT NULL );

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package name

- `version_name (IN) `

  Version name

#### 13.1.6 DROP_PACKAGE_CT

Drops a package by `consistency_token`.

##### Syntax

    procedure DROP_PACKAGE_CT(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       consistency_token IN RAW );

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package name

- `consistency_token (IN) `

  Consistency token

#### 13.1.7 SET_PROFILE

Sets the SQL Translation profile name for a DRDA package.

##### Syntax

    PROCEDURE set_profile(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       profile_name IN VARCHAR2);

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `profile_name`` (IN)`

  SQL Translation profile name

##### Usage Example

    begin
       dbms_drdaas_admin.set_profile ( 'ORACLE', 'MYPACKAGE', 'DB2ZOS');
    end;

#### 13.1.8 SET_LOCALDATE_FORMAT

Sets the Local Date Format to use with a DRDA package.

##### Syntax

    PROCEDURE set_localdate_format(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       date_format IN VARCHAR2);

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `date_format (IN)`

  date format string

##### Usage Example

    begin
       dbms_drdaas_admin.set_localdate_format ( 'ORACLE', 'MYPACKAGE', 'YYYYMMDD');
    end;

#### 13.1.9 SET_LOCALTIME_FORMAT

Sets the local time format to use with a DRDA package.

##### Syntax

    PROCEDURE set_localtime_format(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       time_format IN VARCHAR2);

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `time_format (IN)`

  time format String

##### Usage Example

    begin
       dbms_drdaas_admin.set_localtime_format ( 'ORACLE', 'MYPACKAGE', 'HH:MM:SS');
    end;

#### 13.1.10 SET_TYPEMAP

Sets datatype mapping rules for specific table and column combinations.

##### Syntax

    PROCEDURE set_typemap(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       table_map IN VARCHAR2,
       type_map IN VARCHAR2);

##### Parameters

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `table_map (IN)`

  table and column name expression

- `type_map (IN)`

  numeric type equivalence expression

##### Usage Example

    begin
       dbms_drdaas_admin.set_typemap ( 'ORACLE', 'MYPACKAGE',
          'SYSIBM.SYSPACKSTMT:COUNT(DISTINCT(NAME))', 'NUMBER=INTEGER');
    end;

### 13.2 DBMS_DRDAAS Package

`DBMS_DRDAAS` PL/SQL package manipulates DRDA packages. Use this package to bind new DRDA packages, modify attributes of existing DRDA packages, or drop DRDA packages.

Oracle Database Provider for DRDA uses package `DBMS_DRDAAS` to perform specific DRDA package operations.

#### 13.2.1 DBMS_DRDAAS Privilege Constants

These constants are used with “`GRANT_PRIVILEGE`” and “`REVOKE_PRIVILEGES`” procedures.

##### ALL_PRIVILEGE

This privilege grants all of the above privileges to a client for an Application Package.

##### BIND_PRIVILEGE

This privilege allows a client to bind or rebind an Application Package to the database.

##### COPY_PRIVILEGE

This privilege allows a client to copy an existing Application Package to another name (optionally with different default package options).

##### EXECUTE_PRIVILEGE

This privilege allows a client to execute an existing Application Package.

##### DROP_PRIVILEGE

This privilege allows a client to drop an existing Application Package.

##### SET_PRIVILEGE

This privilege allows a client to set specific Application Package options. See the `SET_``XXX` functions elsewhere in this document.

**Related Topics**

- GRANT_PRIVILEGE
- REVOKE_PRIVILEGE

#### 13.2.2 BIND_PACKAGE

Creates the beginnings of a DRDA package definition.

This is used internally by Oracle Database Provider for DRDA part of `BGNBND` processing.

##### Syntax

    PROCEDURE bind_package(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       version_name IN VARCHAR2 DEFAULT NULL,
       consistency_token IN RAW,
       owner IN VARCHAR2,
       qualifier IN VARCHAR2,
       isolation IN CHAR,
       releaseopt IN CHAR,
       blocking IN CHAR DEFAULT 'N',
       codepage_s IN NUMBER,
       codepage_d IN NUMBER,
       codepage_m IN NUMBER,
       codepage_x IN NUMBER,
       degreeioprl IN NUMBER,
       date_format IN CHAR DEFAULT '3',
       time_format IN CHAR DEFAULT '3',
       decimal_delimiter IN CHAR DEFAULT NULL,
       string_delimiter IN CHAR DEFAULT NULL,
       decprc IN NUMBER,
       charsubtype IN CHAR,
       dynamic_rules IN CHAR DEFAULT NULL,
       reprepdynsql IN CHAR DEFAULT NULL );

##### Parameters

- `collection_id (IN)` is collection ID

- `package_name (IN)` is package name

- `version_name (IN)` is version name (optional, default `NULL`)

- `consistency_token (IN)` is consistency token

- `owner (IN)` is owner of package

- `qualifier (IN)` is default schema

- `isolation (IN)` is isolation level (`R=RR`, `A=ALL`, `C=CS`, `G=CHG`, `N=NC`)

- `releaseopt (IN)` is release package resource option

- `blocking (IN)` is blocking mode (`B=`blocking, `N=`no blocking)

- `codepage_s (IN)` is default codepage (SBCS)

- `codepage_d (IN)` is default codepage (DBCS)

- `codepage_m (IN)` is default codepage (MBCS)

- `codepage_x (IN)` is default codepage (XML)

- `degreeioprl (IN)` is degree of IO parallelism

- `date_format (IN)` is date format (`1=`USA, `2=`EUR, `3=`ISO, `4=`JIS, `5=`Local)

- `time_format (IN)` is time format (`1=`USA, `2=`EUR, `3=`ISO, `4=`JIS, `5=`Local)

- `decimal_delimiter (IN)` is decimal delimiter

- `string_delimiter (IN)` is string delimiter

- `decprc (IN)` is the decimal precision (`15` or `31`)

- `charsubtype (IN)` is character subtype

- `dynamic_rules (IN)` is dynamic rules (future)

- `reprepdynsql (IN)` is prepare dynamic SQL rules again (future)

##### Usage Example

    begin
       dbms_drdaas.bind_package (
          'ORACLE', 'MYPACKAGE', NULL, HEXTORAW('11223344'), 'DRADUSR1',
          'PETER', 'C', 'D', 'B', 1208, 1200, 1208, 1208, 1, '3', '3', '.', '''',
          31, 'M', 'R', 'Y' );
    end;

#### 13.2.3 BIND_STATEMENT

Inserts a statement into DRDA package currently being bound.

This is used internally by Oracle Database Provider for DRDA as part of `BNDSQLSTT` processing.

##### Syntax

    PROCEDURE bind_statement(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       version_name IN VARCHAR2 DEFAULT NULL,
       consistency_token IN RAW,
       statement_assumption IN CHAR,
       statement_no IN NUMBER,
       section_no IN NUMBER,
       statement_len IN NUMBER,
       statement IN CLOB );

##### Parameters

- `collection_id (IN)` is collection Id

- `package_name (IN)` is package name

- `version_name (IN)` is version name (optional, default `NULL`)

- `consistency_token (IN)` is consistency token

- `statement_assumption (IN)` is statement assumption

- `statement_no (IN)` is statement number

- `section_no (IN)` is section number

- `statement_len (IN)` is length of SQL statement text

- `statement (IN)` is statement text

##### Usage Example

    begin
       dbms_drdaas.bind_statement ( 'ORACLE', 'MYPACKAGE', NULL, HEXTORAW('11223344'),
          'C', 1, 1, 42, 'DECLARE CURSOR C1 AS SELECT EMPLOYEE_ID FROM EMPLOYEES' );
    end;

#### 13.2.4 END_BIND

Finalizes a DRDA package currently being bound. (This is used internally by Oracle Database Provider for DRDA as part of `ENDBND` processing.)

##### Syntax

    PROCEDURE end_bind(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       version_name IN VARCHAR2 DEFAULT NULL,
       consistency_token IN RAW,
       max_sections IN NUMBER );

##### Parameters

- `collection_id (IN)` is collection ID

- `package_name (IN)` is package name

- `version_name (IN)` is version name (optional, default `NULL`)

- `consistency_token (IN)` is the consistency token

- `max_sections (IN)` is the maximum number of sections

##### Usage Example

    begin
       dbms_drdaas.end_bind ( 'ORACLE', 'MYPACKAGE', NULL,
          HEXTORAW('11223344'), 1 );
    end;

#### 13.2.5 GRANT_PRIVILEGE

Grants a privilege on a package to a user.

##### Syntax

    PROCEDURE grant_privilege(
       privilege_grant IN PLS_INTEGER,
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       user_name IN VARCHAR2 );

##### Parameters

- `privilege_grant (IN) `

  Privilege to grant

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `user_name (IN)`

  Userid to grant privileges to

##### Usage Example

    begin
       dbms_drdaas.grant_privilege ( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'ORACLE',
         'MYPACKAGE', 'DRDAUSR1' );
    end;

#### 13.2.6 REVOKE_PRIVILEGE

Revokes a privilege from a user for a DRDA package.

##### Syntax

    PROCEDURE revoke_privilege(
       privilege_revoke IN PLS_INTEGER,
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2,
       user_name IN VARCHAR2);

##### Parameters

- `privilege_revoke (IN) `

  Privilege to revoke

- `collection_id (IN) `

  Collection Id

- `package_name (IN) `

  Package Name

- `user_name (IN)`

  Userid to revoke privileges from

##### Usage Example

    begin
       dbms_drdaas.revoke_privilege ( DBMS_DRDAAS_ADMIN.ALL_PRIVILEGE, 'ORACLE',
         'MYPACKAGE', 'DRDAUSR1' );
    end;

#### 13.2.7 DROP_PACKAGE

Drops a DRDA package using the version name.

##### Syntax

    PROCEDURE drop_package(
       collection_id IN VARCHAR2,
       package_name IN VARCHAR2);

##### Parameters

- `collection_id (IN)` is the collection id

- `package_name (IN)` is package name

##### Usage Example

    begin
      dbms_drdaas.drop_package(
        'ORACLE', 'MYPACKAGE');
    end;
