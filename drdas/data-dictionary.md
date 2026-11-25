Oracle enhanced its data dictionary to enable Oracle Database Provider for DRDA.

### 8.1 Data Dictionary Emulation in Oracle Database Provider for DRDA

Many applications use a subset of DB2 system catalogs. Oracle Database Provider for DRDA supports three major sets of catalogs. While all three have some common structures among them, there are many distinct differences.

These catalogs may be implemented as overlays, or views, of existing Oracle data dictionary tables and views.

The catalog described in this section is for “DB2 for z/OS”.

**Related Topics**

- DB2 for z/OS

#### 8.1.1 DB2 for z/OS

DB2 for z/OS includes the following catalog tables. Please see IBM's DB2 for z/OS SQL Reference manual for description of these views.

- `SYSIBM.SYSCOLUMNS`

- `SYSIBM.SYSDUMMY1`

- `SYSIBM.SYSFOREIGNKEYS`

- `SYSIBM.SYSINDEXES`

- `SYSIBM.SYSKEYCOLUSE`

- `SYSIBM.SYSKEYS`

- `SYSIBM.SYSPACKAGE`

- `SYSIBM.SYSPACKSTMT`

- `SYSIBM.SYSPARMS`

- `SYSIBM.SYSPLAN`

- `SYSIBM.SYSRELS`

- `SYSIBM.SYSROUTINES`

- `SYSIBM.SYSSYNONYMS`

- `SYSIBM.SYSTABCONST`

- `SYSIBM.SYSTABLES`

- `SYSIBM.SYSVIEWS`

### 8.2 Data Dictionary Views for Oracle Database Provider for DRDA

Oracle Database Provider for DRDA has uses several data dictionary views:

#### 8.2.1 ALL_DRDAASPACKAGE Data Dictionary View

Table 8-1 contains the list of currently bound DRDA packages. It is owned by user `SYSIBM`. Users must be granted either the `DRDAAS_USER_ROLE` or the `DRDAAS_ADMIN_ROLE` in order to access this view; see “`DRDAAS_USER_ROLE`” and “`DRDAAS_ADMIN_ROLE`”.

Table 8-1 ALL_DRDAASPACKAGE data dictionary view description

| Column Name      | Datatype        | Null?      | Description                               |
|:-----------------|:----------------|:-----------|:------------------------------------------|
| `COLLID`         | `VARCHAR2(128)` | Not `NULL` | collection ID of Pkg (RDBCOLID)           |
| `NAME`           | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)              |
| `VRSNAM`         | `VARCHAR2(128)` |            | version name of package (VRSNAM)          |
| `CONTOKEN`       | `RAW(8)`        | Not `NULL` | consistency string of package (PKGCNSTKN) |
| `OWNER`          | `VARCHAR2(128)` | Not `NULL` | userid that owns package                  |
| `CREATOR`        | `VARCHAR2(128)` | Not `NULL` | userid that created/bound package         |
| `CREATE_TIME`    | `TIMESTAMP`     | Not `NULL` | time package is created                   |
| `LAST_BIND_TIME` | `TIMESTAMP`     | Not `NULL` | time of the last binding of package       |

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)

#### 8.2.2 ALL_DRDAASPACKAUTH Data Dictionary View

Table 8-2 contains the set of user ids, DRDA package names, and privileges granted to the user for each package. It is owned by user `SYSIBM`. Users must be granted either the `DRDAAS_ADMIN_ROLE` or the `DRDAAS_ADMIN_ROLE` in order to access this view; see “`DRDAAS_USER_ROLE`” and “`DRDAAS_ADMIN_ROLE`”.

Table 8-2 ALL_DRDAASPACKAUTH data dictionary view description

| Column Name  | Datatype        | Null?      | Description                              |
|:-------------|:----------------|:-----------|:-----------------------------------------|
| `GRANTOR`    | `VARCHAR2(128)` | Not `NULL` | userid of user who granted privileges    |
| `GRANTEE`    | `VARCHAR2(128)` | Not `NULL` | userid of user who received privileges   |
| `GRANT_TIME` | `TIMESTAMP`     | Not `NULL` | time privileges were created             |
| `COLLID`     | `VARCHAR2(128)` | Not `NULL` | collection ID of DRDA package (RDBCOLID) |
| `NAME`       | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)             |
| `PRIVILEGE`  | `VARCHAR2(128)` | Not `NULL` | privilege                                |

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)

#### 8.2.3 ALL_DRDAASPACKSIDE Data Dictionary View

Table 8-3 shows side attributes for the DRDA package. It is owned by user `SYSIBM`. Users must be granted either the `DRDAAS_ADMIN_ROLE` or the `DRDAAS_ADMIN_ROLE` in order to access this view; refer “`DRDAAS_USER_ROLE`” and “`DRDAAS_ADMIN_ROLE`”.

Table 8-3 ALL_DRDAASPACKSIDE data dictionary view description

| Column Name | Datatype        | Null?      | Description                                       |
|:------------|:----------------|:-----------|:--------------------------------------------------|
| `COLLID`    | `VARCHAR2(128)` | Not `NULL` | collection ID (Schema) of DRDA package (RDBCOLID) |
| `NAME`      | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)                      |
| `SIDEITEM`  | `VARCHAR2(128)` | Not `NULL` | side item                                         |
| `SIDEWORD`  | `VARCHAR2(255)` | Not `NULL` | side keyword                                      |
| `SIDEVALUE` | `VARCHAR2(255)` | Not `NULL` | side value                                        |

**Related Topics**

- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)
- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)

#### 8.2.4 DBA_DRDAASPACKAGE Data Dictionary View

Table 8-4 contains the DRDA package definition data. It is owned by user `SYSIBM`. Users must be granted the `DRDAAS_ADMIN_ROLE` in order to access this view; see “`DRDAAS_ADMIN_ROLE`”.

Table 8-4 DBA_DRDAASPACKAGE data dictionary view description

| Column Name      | Datatype        | Null?      | Description                                          |
|:-----------------|:----------------|:-----------|:-----------------------------------------------------|
| `COLLID`         | `VARCHAR2(128)` | Not `NULL` | collection ID (Schema) of DRDA package (RDBCOLID)    |
| `NAME`           | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)                         |
| `VRSNAM`         | `VARCHAR2(128)` |            | version name of package (VRSNAM)                     |
| `CONTOKEN`       | `RAW(8)`        | Not `NULL` | consistency string of package (PKGCNSTKN)            |
| `OWNER`          | `VARCHAR2(128)` | Not `NULL` | userid that owns package                             |
| `CREATOR`        | `VARCHAR2(128)` | Not `NULL` | userid that created package                          |
| `CREATE_TIME`    | `TIMESTAMP`     | Not `NULL` | time package is created                              |
| `LAST_BIND_TIME` | `TIMESTAMP`     | Not-`NULL` | time of the last binding of package                  |
| `QUALIFIER`      | `VARCHAR2(128)` |            | default schema of package (DFTRDBCOL)                |
| `PKSIZE`         | `NUMBER(5)`     | Not `NULL` | number of sections in the package (MAXSCTNBR)        |
| `VALID`          | `CHAR(1)`       | Not `NULL` | package valid state; `Y` for yes, `N` for no         |
| `ISOLATION`      | `CHAR(1)`       | Not `NULL` | `R=RR`, `A=ALL`, `C=CS`, `G=CHG`, `N=NC` (PKGISOLVI) |
| `RELEASEOPT`     | `CHAR(1)`       |            | `C`=`COMMIT`, `D`=`DEALLOCATE` (RDBRLSOPT)           |
| `BLOCKING`       | `CHAR(1)`       |            | `B=`block, `N=`no blocking (QRYBLKCTL)               |
| `CODEPAGES`      | `NUMBER(5)`     |            | default DBCS codepage (PKGDFTCC(CCSIDSBC))           |
| `CODEPAGED`      | `NUMBER(5)`     |            | Default DBCS codepage (PKGDFTCC(CCSIDDBC))           |
| `CODEPAGEM`      | `NUMBER(5)`     |            | Default MBCS codepage (PKGDFTCC(CCSIDMBC))           |
| `CODEPAGEX`      | `NUMBER(5)`     |            | Default XML codepage (PKGDFTCC(CCSIDXML))            |
| `DEGREEIOPRL`    | `NUMBER(5)`     |            | Degree of parallel I/O (DGRIOPRL)                    |
| `DATEFMT`        | `CHAR(1)`       |            | Date Format, 1=USA, 2=EUR, 3=ISO, 4JIS, 5=LOCAL      |
| `TIMEFMT`        | `CHAR(1)`       |            | Time Format, 1=USA, 2=EUR, 3=ISO, 4JIS, 5=LOCAL      |
| `DECDEL`         | `CHAR(1)`       |            | Decimal Delimiter (STTDECDEL)                        |
| `STRDEL`         | `CHAR(1)`       |            | String Delimiter (STTSTRDEL)                         |
| `DECPRC`         | `NUMBER(5)`     |            | Decimal Precision (DECPRC)                           |
| `CHARSUBTYPE`    | `CHAR(1)`       |            | Character Subtype (PKGDFTCST)                        |
| `DYNAMICRULES`   | `CHAR(1)`       |            | Future usage (PKGATHRUL)                             |
| `REPREPDYNSQL`   | `CHAR(1)`       |            | Future usage (PRPSTTKP)                              |

**Related Topics**

- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)

#### 8.2.5 DBA_DRDAASPACKAUTH Data Dictionary View

Table 8-5 contains the set of userids and RDA package names, as well as privileges granted to the user for each package. It is owned by user `SYSIBM`. Users must be granted the `DRDAAS_ADMIN_ROLE` in order to access this view; see “`DRDAAS_ADMIN_ROLE`”.

Table 8-5 DBA_DRDAASPACKAUTH data dictionary view description

| Column Name | Datatype        | Null?      | Description                                            |
|:------------|:----------------|:-----------|:-------------------------------------------------------|
| `GRANTOR`   | `VARCHAR2(128)` | Not `NULL` | authorization ID of user who grants package privileges |
| `GRANTEE`   | `VARCHAR2(128)` | Not `NULL` | authorization ID of user who has package privileges    |
| `COLLID`    | `VARCHAR2(128)` | Not `NULL` | collection ID (Schema) of DRDA package (RDBCOLID)      |
| `NAME`      | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)                           |
| `VRSNAM`    | `VARCHAR(128)`  | Not `NULL` | version name of package (VRSNAM)                       |
| `PRIVILEGE` | `VARCHAR2(128)` | Not `NULL` | granted privilege                                      |

**Related Topics**

- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)

#### 8.2.6 DBA_DRDAASPACKSIDE Data Dictionary View

Table 8-6 shows side attributes for the DRDA package. It is owned by user `SYSIBM`. Users must have `DRDAAS_ADMIN_ROLE` in order to access this view.

Table 8-6 DBA_DRDAASPACKSIDE data dictionary view description

| Column Name | Datatype        | Null?      | Description                                       |
|:------------|:----------------|:-----------|:--------------------------------------------------|
| `COLLID`    | `VARCHAR2(128)` | Not `NULL` | collection ID (Schema) of DRDA package (RDBCOLID) |
| `NAME`      | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)                      |
| `SIDEITEM`  | `VARCHAR(128)`  | Not `NULL` | side item                                         |
| `SIDEWORD`  | `VARCHAR2(255)` | Not `NULL` | side keyword                                      |
| `SIDEVALUE` | `VARCHAR2(255)` | Not `NULL` | side value                                        |

#### 8.2.7 DBA_DRDAASPACKSTMT Data Dictionary View

Table 8-7 contains the DRDA package body data. It is owned by user `SYS`. Users must be granted the `DRDAAS_ADMIN_ROLE` in order to access this view; see “`DRDAAS_ADMIN_ROLE`”.

Table 8-7 DBA_DRDAASPACKSTMT data dictionary view description

| Column Name | Datatype        | Null?      | Description                                       |
|:------------|:----------------|:-----------|:--------------------------------------------------|
| `COLLID`    | `VARCHAR2(128)` | Not `NULL` | collection ID (Schema) of DRDA package (RDBCOLID) |
| `NAME`      | `VARCHAR2(128)` | Not `NULL` | name of DRDA package (PKGID)                      |
| `VRSNAM`    | `VARCHAR(128)`  |            | version name of package (VRSNAM)                  |
| `CONTOKEN`  | `RAW(8)`        | Not `NULL` | consistency string of package (PKGCNSTKN)         |
| `STMTASM`   | `CHAR(1)`       | Not `NULL` | Statement Assumptions (BNDSTTADM)                 |
| `STMTNO`    | `NUMBER(5)`     | Not `NULL` | statement number (SQLSTTNBR)                      |
| `SECTNO`    | `NUMBER(5)`     | Not `NULL` | section number (PKGSN)                            |
| `STMTLEN`   | `NUMBER`        | Not `NULL` | statement text length                             |
| `STMT`      | `CLOB`          | Not `NULL` | statement text                                    |

**Related Topics**

- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)

#### 8.2.8 DBA_DRDAASTRACE Data Dictionary View

“`DRDAASPATRACE` data dictionary view description contains trace entry from the `DBMS_DRDAAS` and `DBMS_DRDAAS_ADMIN `package functions. It is owned by user `SYSIBM`.Users must be granted either the `DRDAAS_ADMIN_ROLE` or the `DRDAAS_ADMIN_ROLE` in order to access this view.

This is a debugging feature only.

Table 8-8 DBA_DRDAASPATRACE data dictionary view description

| Column Name | Datatype        | Null?      | Description                               |
|:------------|:----------------|:-----------|:------------------------------------------|
| `CALLER`    | `VARCHAR2(128)` | Not `NULL` | userid of user who wrote the trace record |
| `FUNC`      | `VARCHAR2(128)` | Not `NULL` | function that is traced                   |
| `ARG1`      | `VARCHAR(128)`  |            | argument 2                                |
| `ARG2`      | `VARCHAR(128)`  |            | argument 1                                |
| `ARG3`      | `VARCHAR(128)`  |            | argument 3                                |
| `ARG4`      | `VARCHAR(128)`  |            | argument 4                                |
| `ARG5`      | `VARCHAR(128)`  |            | argument 5                                |
| TS          | `TIMESTAMP`     | Not-`NULL` | timestamp of trace entry                  |

**Related Topics**

- [DRDAAS_ADMIN_ROLE](security-and-storage-considerations.md)
- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)

#### 8.2.9 USER_DRDAASPACKAGE Data Dictionary View

The view only returns rows that match the current SQL user ID in the `creator` or `owner` column and have `EXECUTE_PRIVILEGE` granted to the userid in `DBA_DRDAASPACKAUTH` matching the package `COLLID` and `name`.

The view `USER_DRDAASPACKAGE` maps onto `DBA_DRDAASPACKAGE` table. It is owned by user `SYSIBM`. Users must have the `DRDAAS_USER_ROLE` in order to select from this view; see “`DRDAAS_USER_ROLE`”.

This view has the same column definition as the `DBA_DRDAASPACKAGE` table; see “DBA_DRDAASPACKAGE data dictionary view description.”

**Related Topics**

- DBA_DRDAASPACKAGE Data Dictionary View

#### 8.2.10 USER_DRDAASPACKAUTH Data Dictionary View

This view only return rows that match the current SQL user ID in the `grantee` column.

The view `USER_DRDAASPACKAUTH` maps on top of `DBA_DRDAASPACKAUTH`. It is owned by user `SYSIBM`. Users must have the `DRDAAS_USER_ROLE` in order to select from this table; see “`DRDAAS_USER_ROLE`”.

This view has the same column definition as the `DBA_DRDAASPACKAUTH` table; see “`DBA_DRDAASPACKAUTH` data dictionary view description”.

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- DBA_DRDAASPACKAUTH Data Dictionary View

#### 8.2.11 USER_DRDAASPACKSIDE Data Dictionary View

This view is used internally by the Application Server.

The view `USER_DRDAASPACKSIDE` maps on top of `DBA_DDRDAASPACKSIDE`. It is owned by user `SYSIBM`. Users must have the `DRDAAS_USER_ROLE` in order to select from this table; see “`DRDAAS_USER_ROLE`”.

This view has the same column definition as the `DBA_DRDAASPACKSIDE` table; see “`DBA_DRDAASPACKSIDE` data dictionary view description”.

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- DBA_DRDAASPACKSIDE Data Dictionary View

#### 8.2.12 USER_DRDAASPACKSTMT Data Dictionary View

The view only returns rows that match the current SQL user ID in the `creator` or `owner` column, and have `EXECUTE_PRIVILEGE` granted to the userid in `DBA_DRDAASPACKAUTH` matching the package `COLLID` and `name`.

The view `USER_DRDAASPACKSTMT` maps onto of `DBA_DRDAASPACKSTMT` table. It is owned by user `SYSIBM`. Users must have the `DRDAAS_USER_ROLE` in order to select from this table; see “`DRDAAS_USER_ROLE`”.

This view has the same column definition as the `DBA_DRDAASPACKSTMT` table; see “`DBA_DRDAASPACKSTMT` data dictionary view description.”

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- DBA_DRDAASPACKSTMT Data Dictionary View

#### 8.2.13 USER_DRDAASTRACE Data Dictionary View

The view returns only the rows that match the userid of the current user.

This is a debugging feature only.

The view `USER_DRDAASTRACE` maps onto `DBA_DRDAASTRACE` view. It is owned by user `SYSIBM`. Users must be granted the `DRDAAS_USER_ROLE` in order to access this view; see “`DRDAAS_USER_ROLE`”.

This view has the same column definition as the `USER_DRDAASTRACE` view, with the exception of the `caller` column. See “`DBA_DRDAASPATRACE` data dictionary view”.

**Related Topics**

- [DRDAAS_USER_ROLE](security-and-storage-considerations.md)
- DBA_DRDAASTRACE Data Dictionary View
