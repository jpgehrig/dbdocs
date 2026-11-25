Before using Oracle Database Provider for DRDA to transition DB2 DRDA applications to Oracle, several security and storage issues must be considered.

### 11.1 Overview of Security and Storage for Oracle Database Provider for DRDA

Oracle Database Provider for DRDA uses the security and authorization models of the Oracle Database; this ensures correct SQL access to user data.

DRDA specifies two primary authorization models: `REQUESTER` and `OWNER`. They are specified as attribute of the package, `PKGATHRUL`.

- In the `REQUESTER` model, currently logged-in user is the authorization control.

  The `REQUESTER` model is also called Dynamic SQL Rules, and it is used for executing the SQL that is constructed at runtime. This is the security model that Oracle Database implements for SQL access.

- In the `OWNER` model, a stored `USERID` (package owner, `PKGOWNID`) instantiates a different `USERID` for the duration of the statement execution.

  The `OWNER` model is also called Static SQL Rules, and it is used for pre-bound SQL within the package. Oracle Database does not implement an equivalent security model.

Because Oracle Database only implements one security model, all SQL within a package, both stored and dynamically created, is executed under the Dynamic SQL Rules model. This does not override the instantiation modes of any PL/SQL objects created with the `AUTHID DEFINER` attribute.

See Oracle® Database PL/SQL Language Reference for details about `AUTHID DEFINER`.

### 11.2 Authentication and Encryption in Oracle Database Provider for DRDA

DRDA requires that user authentication (ACCSEC(SECMEC), SECCHK) be performed before any access to the database (ACCRDB) may be performed.

#### 11.2.1 Authentication Services

DRDA provides two types of services for authentication: dedicated use, and multiplexed use.

- Under dedicated use, the AS provides access to a single, dedicated database, without an option to connect to another database. The rdbnam passed later in the ACCRDB must match the target database name; otherwise, the session access fails with an RDBAFLRM message.

  In this mode, the ACCSEC does not require the rdbnam instance variable to perform authentication because there is no choice to be made between databases. Thus, the AS is free to make a session association with the single database at the time of ACCSEC processing, and to verify that the requested security mechanism (SECMEC) is available. When the SECCHK command is sent, the initial database session is maintained and full authentication is performed.

  This mode must be used with older ARs that do not support multiplexed servers. If the AR supplies the rdbnam in this mode, it must be validated against the connected database.

- Under multiplexed mode, the AS provides access to many databases at the same time. In this mode, the rdbnam instance variable in the ACCSEC is required to validate the requested security mechanism. The AS connects to the requested database for security validation. When the SECCHK command is sent, the initial database session is maintained and full authentication is performed.

  This mode is supported with newer ARs, which supply the rdbnam as part of the ACCSEC. If the AR does not supply the rdbnam in the ACCSEC in this mode, it generates an error and an RDBAFLRM response is sent to the ACCSEC.

#### 11.2.2 Encryption Services

Oracle Database Provider for DRDA supports the following security mechanisms:

- EUSRIDPWD – Encrypted User ID and Password Mechanism

- EUSRIDNWPWD – Encrypted User ID, Password, and New Password Mechanism

- USRIDPWD – User ID and Password Mechanism

- USRIDNWPWD – User ID, Password, and New Password Mechanism

- USRENCPWD – User ID and Password Encrypted Mechanism

After the security mechanisms are verified as accessible, the actual security authorization (SECCHK) can proceed.

### 11.3 Database Roles in Oracle Database Provider for DRDA

Oracle Database Provider for DRDA uses the following two roles: `DRDAAS_ADMIN_ROLE` and `DRDAAS_USER_ROLE`.

#### 11.3.1 DRDAAS_ADMIN_ROLE

The `DRDAAS_ADMIN_ROLE` role allows access to and use of the `DBMS_DRDAAS_ADMIN` package. It is a DBA-level privilege specific to Oracle Database Provider for DRDA. Administrators who manage remote DRDA access to the Oracle database must be granted this role.

#### 11.3.2 DRDAAS_USER_ROLE

The `DRDAAS_USER_ROLE` role permits an Oracle Database Provider for DRDA user access to the `DBMS_DRDAAS` package for the following purposes:

- For binding a DRDA package

- For permitting read access to Oracle Database Provider for DRDA package resource tables

- For package execution

Without the privileges of the `DRDAAS_USER_ROLE` role, Oracle Database Provider for DRDA user is unable to execute DRDA packages to which they have granted access.

### 11.4 Storage in Oracle Database Provider for DRDA

Oracle Database Provider for DRDA users have allocated storage named `SYSIBM`. This is implemented by the `SYSIBM` tablespace and `SYSIBM` user.

#### 11.4.1 SYSIBM Tablespace

All tables, views and packages supplied and used by the Application Server for management and support functions are in the tablespace `SYSIBM`. This tablespace must be created before installing Oracle Database Provider for DRDA support packages. An example of how to create the `SYSIBM` tablespace is the `catdrdaas.sql` script supplied with the product. See the listing for “catdrdaas.sql” in “Scripts for Creating and Maintaining Oracle Database Provider for DRDA”.

    create tablespace SYSIBM datafile 'sysibm01.dbf' size 70M reuse
       extent management local segment space management auto online;

**Related Topics**

- [catdrdaas.sql](scripts-to-create-and-maintain-database-provider-for-DRDA.md)
- [Scripts for Creating and Maintaining Oracle Database Provider for DRDA](scripts-to-create-and-maintain-database-provider-for-DRDA.md)

#### 11.4.2 SYSIBM User

All tables, views, and packages supplied and used by Oracle Database Provider for DRDA are under the user schema `SYSIBM`. As part of the installation of Oracle Database Provider for DRDA packages and tables, this user id is created as a locked account, and is set to use the `SYSIBM` tablespace for its storage.
