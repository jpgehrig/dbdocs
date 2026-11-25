## 128 DBMS_PDB_ALTER_SHARING

In an application container with a pre-installed application, the `DBMS_PDB_ALTER_SHARING` package provides an interface to set database objects as application common objects or to specify that a database object is not an application common object.

**Note:**

This package provides a subset of the subprograms in the `DBMS_PDB` package. Users who do not have `EXECUTE` privilege on the `DBMS_PDB` package can be granted `EXECUTE` privilege on this package to run these subprograms.

**See Also:**

- [Oracle Database Administrator's Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container

- [Oracle XML DB Developer's Guide](../adxdb/administration-of-XML-DB.md) for information about configuring protocol ports and DNS mappings

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-PLUGGABLE-DATABASE.md) for information about creating PDBs

- [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) regarding how to create audit policies in a multitenant environment

This chapter contains the following topics:

- DBMS_PDB_ALTER_SHARING Overview

- DBMS_PDB_ALTER_SHARING Security Model

- Summary of DBMS_PDB_ALTER_SHARING Subprograms

### 128.1 DBMS_PDB_ALTER_SHARING Overview

The subprograms in this package can set a database object to one of the following types of application common objects in an application container: data-linked object, extended data-linked object, or metadata-linked object.

A data-linked application common object stores data in the application root that can be accessed and modified by all of the application PDBs in the application container. For an extended data-linked object, each application PDB can create its own specific data while sharing the common data in the application root. Therefore, with an extended data-linked object, only the data stored in the application root is common for all application PDBs. A metadata-linked application common object stores the metadata for the specific object, such as a table, in the application root, so that the containers in the application container have the same structure for the object but different data. This package also contains a procedure that specifies that a database object is not an application common object.

You can use the subprograms in this package when you

Typically, the subprograms in this package are used in the following cases:

- An application that is installed in a PDB is migrated to an application container. The application can be migrated to the application root or to an application PDB. For example, you can migrate an application installed in a PDB plugged into an Oracle Database 12c Release 1 (12.1) CDB to an application container in an Oracle Database 12c Release 2 (12.2) CDB.

- An application is installed in an application root using an installation program that does not allow setting application common objects.

**See Also:**

[Oracle Database Administrator's Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container

### 128.2 DBMS_PDB_ALTER_SHARING Security Model

This package provides a subset of the subprograms in the `DBMS_PDB` package. User who do not have `EXECUTE` privilege on the `DBMS_PDB` package can be granted `EXECUTE` privilege on this package to run these subprograms.

Security on this package can be controlled in either of the following ways:

- Granting `EXECUTE` on this package to selected users or roles.

- Granting `EXECUTE_CATALOG_ROLE` to selected users or roles.

If subprograms in the package are run from within a stored procedure, then the user who runs the subprograms must be granted `EXECUTE` privilege on the package directly. It cannot be granted through a role.

### 128.3 Summary of DBMS_PDB_ALTER_SHARING Subprograms

This table lists and briefly describes `DBMS_PDB_ALTER_SHARING` package subprograms.

Table 128-1 DBMS_PDB_ALTER_SHARING Subprograms

| Subprogram                     | Description                                                                  |
|:-------------------------------|:-----------------------------------------------------------------------------|
| SET_DATA_LINKED Procedure      | Sets a database object to a data-linked application common object            |
| SET_EXT_DATA_LINKED Procedure  | Sets a database object to an extended data-linked application common object  |
| SET_METADATA_LINKED Procedure  | Sets a database object to a metadata-linked application common object        |
| SET_PROFILE_EXPLICIT Procedure | Sets a profile as an application common profile in an application container. |
| SET_ROLE_EXPLICIT Procedure    | Sets a role as an application common role in an application container.       |
| SET_USER_EXPLICIT Procedure    | Sets a local user as an application common user in an application container. |

#### 128.3.1 SET_DATA_LINKED Procedure

This procedure sets a database object to a data-linked application common object. In an application container, data-linked application common objects store data in the application root only, and the data can be accessed by all of the application PDBs in the application container. The data in a data-linked application common object can be modified only in the application root.

You can use this procedure to set data-linked application common objects when you migrate an application that is installed in a PDB to an application container. The application can be migrated to the application root or to an application PDB. For example, you can migrate an application installed in a PDB plugged into an Oracle Database 12c Release 1 (12.1) CDB to an application container in an Oracle Database 12c Release 2 (12.2) CDB.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_DATA_LINKED (
       schema_name  IN VARCHAR2,
       object_name  IN VARCHAR2,
       namespace    IN NUMBER,
       edition_name IN VARCHAR2  DEFAULT NULL);

##### Parameters

Table 128-2 SET_DATA_LINKED Procedure Parameters

| Parameter      | Description                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `schema_name`  | The name of the schema that owns the database object.                                                                       |
| `object_name`  | The name of the database object.                                                                                            |
| `namespace`    | The namespace of the database object.<br>The `NAMESPACE` column of the `DBA_OBJECTS` view shows the namespace of an object. |
| `edition_name` | The name of the edition for the database object.                                                                            |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container

#### 128.3.2 SET_EXT_DATA_LINKED Procedure

This procedure sets a database object to an extended data-linked application common object. In an application container, for an extended data-linked object, each application PDB can create its own specific data while sharing the common data in the application root. Therefore, only the data stored in the application root is common for all application PDBs.

You can use this procedure to set extended data-linked application common objects when you migrate an application that is installed in a PDB to an application container. The application can be migrated to the application root or to an application PDB. For example, you can migrate an application installed in a PDB plugged into an Oracle Database 12c Release 1 (12.1) CDB to an application container in an Oracle Database 12c Release 2 (12.2) CDB.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_EXT_DATA_LINKED (
       schema_name  IN VARCHAR2,
       object_name  IN VARCHAR2,
       namespace    IN NUMBER,
       edition_name IN VARCHAR2  DEFAULT NULL);

##### Parameters

Table 128-3 SET_EXT_DATA_LINKED Procedure Parameters

| Parameter      | Description                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `schema_name`  | The name of the schema that owns the database object.                                                                       |
| `object_name`  | The name of the database object.                                                                                            |
| `namespace`    | The namespace of the database object.<br>The `NAMESPACE` column of the `DBA_OBJECTS` view shows the namespace of an object. |
| `edition_name` | The name of the edition for the database object.                                                                            |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container

#### 128.3.3 SET_METADATA_LINKED Procedure

This procedure sets a database object to a metadata-linked application common object. In an application container, metadata-linked application common objects store the metadata for specific objects, such as tables, so that the containers that share the application common object have the same structure but different data.

You can use this procedure to set metadata-linked application common objects when you migrate an application that is installed in a PDB to an application container. The application can be migrated to the application root or to an application PDB. For example, you can migrate an application installed in a PDB plugged into an Oracle Database 12c Release 1 (12.1) CDB to an application container in an Oracle Database 12c Release 2 (12.2) CDB.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_METADATA_LINKED (
       schema_name  IN VARCHAR2,
       object_name  IN VARCHAR2,
       namespace    IN NUMBER,
       edition_name IN VARCHAR2  DEFAULT NULL);

##### Parameters

Table 128-4 SET_METADATA_LINKED Procedure Parameters

| Parameter      | Description                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `schema_name`  | The name of the schema that owns the database object.                                                                       |
| `object_name`  | The name of the database object.                                                                                            |
| `namespace`    | The namespace of the database object.<br>The `NAMESPACE` column of the `DBA_OBJECTS` view shows the namespace of an object. |
| `edition_name` | The name of the edition for the database object.                                                                            |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container

#### 128.3.4 SET_PROFILE_EXPLICIT Procedure

This procedure sets a profile as an application common profile in an application container. This procedure is intended for migrating a profile from a previous release to an application container in the current release.

This procedure must be invoked in an application install, patch, upgrade, or uninstall operation in an application root.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_PROFILE_EXPLICIT (
       profile_name IN VARCHAR2);

##### Parameters

Table 128-5 SET_PROFILE_EXPLICIT Procedure Parameters

| Parameter      | Description              |
|:---------------|:-------------------------|
| `profile_name` | The name of the profile. |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container.

#### 128.3.5 SET_ROLE_EXPLICIT Procedure

This procedure sets a role as an application common role in an application container. This procedure is intended for migrating a role from a previous release to an application container in the current release.

This procedure must be invoked in an application install, patch, upgrade, or uninstall operation in an application root.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_ROLE_EXPLICIT (
       role_name IN VARCHAR2);

##### Parameters

Table 128-6 SET_ROLE_EXPLICIT Procedure Parameters

| Parameter   | Description           |
|:------------|:----------------------|
| `role_name` | The name of the role. |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container.

#### 128.3.6 SET_USER_EXPLICIT Procedure

This procedure sets a local user as an application common user in an application container.

This procedure must be invoked in an application install, patch, upgrade, or uninstall operation in an application root.

##### Syntax

    DBMS_PDB_ALTER_SHARING.SET_USER_EXPLICIT (
       user_name IN VARCHAR2);

##### Parameters

Table 128-7 SET_USER_EXPLICIT Procedure Parameters

| Parameter   | Description           |
|:------------|:----------------------|
| `user_name` | The name of the user. |

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-application-containers-with-sql-plus.md) for information about migrating an application to an application container.
