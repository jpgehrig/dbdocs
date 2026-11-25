## 138  DBMS_QOPATCH

The `DBMS_QOPATCH` package provides an interface to view the installed database patches.

This chapter contains the following topics:

- Overview

- Security Modell

- Operational Notes

- Error Messages

- Summary of DBMS_QOPATCH Subprograms

### 138.1 DBMS_QOPATCH Overview

The `DBMS_QOPATCH` package provides a PLSQL/SQL interface to view the installed database patches. The interface provides all the patch information available as part of the `OPATCH LSINVENTORY -XML` command. The package accesses the OUI patch inventory in real time to provide patch and meta-information.

### 138.2 DBMS_QOPATCH Security Model

The `DBMS_QOPATCH` package is created as part of SYS schema and SYS is the only user who can execute these subprograms.

### 138.3 DBMS_QOPATCH Operational Notes

The following operational notes apply to DBMS_QOPATCH.

- The package will work only if the database is `OPEN`.

- In an Oracle Real Application Clusters (RAC) environment, if the subprogram requires to fetch data from other RAC nodes it spawns a job in the other node(s) to get the data. In this case `JOB_QUEUE_PROCESSES` needs to be` >0` for the package to fetch the data from other RAC nodes.

- If there is a delay in the job execution, the package returns `ORA-20008` error.

### 138.4 DBMS_QOPATCH Exceptions

This table lists the exceptions raised by the `DBMS_QOPATCH` package.

Table 138-1 DBMS_QOPATCH Error Messages

| Error Code  | Description                                                              |
|:------------|:-------------------------------------------------------------------------|
| `ORA-20001` | Latest XML inventory is not loaded into table.                           |
| `ORA-20002` | Directory creation failed.                                               |
| `ORA-20003` | Configuration of a job on a node failed.                                 |
| `ORA-20004` | Job configuration failed as node is inactive.                            |
| `ORA-20005` | Job is not configured with given node, instance name.                    |
| `ORA-20006` | Number of RAC active instances and opatch jobs configured are not same.  |
| `ORA-20007` | Job configuration failed as node or instance is not active.              |
| `ORA-20008` | Timed out - job execution time is more than 120Secs.                     |
| `ORA-20009` | Job execution failed.                                                    |
| `ORA-20010` | Node is inactive and job cannot be executed.                             |
| `ORA-20011` | Job name is `NULL` and inventory cannot be loaded.                       |
| `ORA-20012` | `JOB_QUEUE_PROCESSES` is set to zero and the inventory cannot be loaded. |
| `ORA-20013` | `DBMS_QOPATCH` ran mostly in non-install area.                           |
| `ORA-20014` | Database is not opened.                                                  |
| `ORA-20015` | Database opened as read-only.                                            |

### 138.5 Summary of DBMS_QOPATCH Subprograms

This table lists and briefly describes the `DBMS_QOPATCH` package subprograms.

Table 138-2 DBMS_QOPATCH Package Subprograms

| Subprogram                       | Description                                                                                                                                                               |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHECK_PATCH_INSTALLED Function   | Checks if a patch is installed.                                                                                                                                           |
| GET_OPATCH_BUGS Function         | Provides a bugs list for a patch in XML format if the patch number is given. If patch is not given then it lists all the bugs installed in all the patches in XML format. |
| GET_OPATCH_COUNT Function        | Provides the total number of installed patches in XML format                                                                                                              |
| GET_OPATCH_DATA Function         | Provides top level patch information for the patch (such as Patch ID, patch creation time) in the XML element                                                             |
| GET_OPATCH_FILES Function        | Provides the list of files modified in the given patch number in XML format                                                                                               |
| GET_OPATCH_INSTALL_INFO Function | Returns the XML element containing the `ORACLE_HOME` details such as patch and inventory location                                                                         |
| GET_OPATCH_LIST Function         | Provides list of patches installed as an XML element from the XML inventory                                                                                               |
| GET_OPATCH_LSINVENTORY           | Returns whole opatch inventory as XML instance document.                                                                                                                  |
| GET_OPATCH_OLAYS Function        | Provides overlay patches for a given patch as XML element                                                                                                                 |
| GET_OPATCH_PREQS Function        | Provides prerequisite patches for a given patch as XML element                                                                                                            |
| GET_OPATCH_XSLT                  | Returns the style-sheet for the opatch XML inventory presentation                                                                                                         |
| GET_PATCH_DETAILS Function       | Displays the detailed patch information from `opatch lsinventory`.                                                                                                        |
| GET_SQLPATCH_STATUS Procedure    | Displays the SQL patch status by querying from SQL patch registry to produce complete patch level information                                                             |
| IS_PATCH_INSTALLED Function      | Provides information (such as patchID, application date, and SQL patch information) on the installed patch as XML node by querying the XML inventory                      |
| OPATCH_COMPARE_CURRENT Function  | Compares the current database with a list of bugs.                                                                                                                        |
| OPATCH_COMPARE_NODES Function    | Compares the given RAC node(s) with the instance to the present connected node with current node. The return value indicates whether the data was refreshed or not.       |
| SET_CURRENT_OPINST Procedure     | Sets the node name and instance to get the inventory details specific to it in an Oracle Real Application Clusters (RAC) environment                                      |

#### 138.5.1 CHECK_PATCH_INSTALLED Function

Checks if the patch is installed.

##### Syntax

    DBMS_QOPATCH.CHECK_PATCH_INSTALLED (
       bugs     IN QOPATCH_LIST);
     RETURN VARCHAR2;

##### Parameters

Table 138-3 CHECK_PATCH_INSTALLED Parameters

| Parameter | Description                    |
|:----------|:-------------------------------|
| `bugs`    | List of patches to be checked. |

#### 138.5.2 GET_OPATCH_BUGS Function

This function provides a bugs list in a patch if the patch number is given. If a patch number is not given, it lists all the bugs in the specified XML format.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_BUGS (
       patchnum IN VARCHAR2 DEFAULT NULL);
     RETURN XMLTYPE;

##### Parameters

Table 138-4 GET_OPATCH_BUGS Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.3 GET_OPATCH_COUNT Function

This function provides the total number of installed patches in XML format.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_COUNT (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-5 GET_OPATCH_COUNT Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.4 GET_OPATCH_DATA Function

This function provides top level patch information for the patch (such as Patch ID, patch creation time) in the XML element.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_DATA (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-6 GET_OPATCH_DATA Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.5 GET_OPATCH_FILES Function

This function provides the list of files modified in the given patch number in XML format.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_FILES (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-7 GET_OPATCH_FILES Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.6 GET_OPATCH_INSTALL_INFO Function

This function returns the XML element containing the `ORACLE_HOME` details such as patch and inventory location.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_INSTALL_INFO
     RETURNS XMLTYPE;

#### 138.5.7 GET_OPATCH_LIST Function

This function provides list of patches installed as an XML element from the XML inventory.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_LIST
     RETURN XMLTYPE;

#### 138.5.8 GET_OPATCH_LSINVENTORY

This function returns whole opatch inventory as XML instance document.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_LSINVENTORY
     RETURN XMLTYPE;

#### 138.5.9 GET_OPATCH_OLAYS Function

This function provides overlay patches for a given patch as XML element.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_OLAYS (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-8 GET_OPATCH_OLAYS Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.10 GET_OPATCH_PREQS Function

This function provides prerequisite patches for a given patch as XML element.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_PREQS (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-9 GET_OPATCH_PREQS Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.11 GET_OPATCH_XSLT

This function returns the style-sheet for the opatch XML inventory presentation. You can use the return type of this subprogram to perform XMLTRANSFORM and the transformed result has the same appearance as opatch text output.

##### Syntax

    DBMS_QOPATCH.GET_OPATCH_XSLT
     RETURN XMLTYPE;

#### 138.5.12 GET_PATCH_DETAILS Function

Displays the detailed patch information from `opatch lsinventory`.

##### Syntax

    DBMS_QOPATCH.GET_PATCH_DETAILS (
       patch    IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-10 GET_PATCH_DETAILS Function Parameters

| Parameter | Description       |
|:----------|:------------------|
| `patch`   | The patch number. |

#### 138.5.13 GET_SQLPATCH_STATUS Procedure

This procedure displays the SQL patch status by querying from SQL patch registry to produce complete patch level information. If the patch number is given, it displays the information specific to the given SQL patch, otherwise information for all SQL patches.

##### Syntax

    DBMS_QOPATCH.GET_SQLPATCH_STATUS (
       patchnum IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 138-11 GET_SQLPATCH_STATUS Procedure Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.14 IS_PATCH_INSTALLED Function

This function provides information (such as patchID, application date, and SQL patch information) on the installed patch as XML node by querying the XML inventory.

##### Syntax

    DBMS_QOPATCH.IS_PATCH_INSTALLED (
       patchnum IN VARCHAR2);
     RETURN XMLTYPE;

##### Parameters

Table 138-12 IS_PATCH_INSTALLED Function Parameters

| Parameter  | Description  |
|:-----------|:-------------|
| `patchnum` | Patch number |

#### 138.5.15 OPATCH_COMPARE_CURRENT Function

Compares the current database with a list of bugs.

##### Syntax

    DBMS_QOPATCH.OPATCH_COMPARE_CURRENT Function (
       bugs     IN QOPATCH_LIST);
     RETURN VARCHAR2;

##### Parameters

Table 138-13 OPATCH_COMPARE_CURRENT Function Parameters

| Parameter | Description                                        |
|:----------|:---------------------------------------------------|
| `bugs`    | List of bugs to compare with the current database. |

#### 138.5.16 OPATCH_COMPARE_NODES Function

Compares the given RAC node(s) with the instance to the present connected node with current node. The return value indicates whether the data was refreshed or not.

##### Syntax

    DBMS_QOPATCH.OPATCH_COMPARE_NODES (
       node     IN VARCHAR2 DEFAULT NULL,
       inst     IN VARCHAR2 DEFAULT NULL);
     RETURN VARCHAR2;

##### Parameters

Table 138-14 OPATCH_COMPARE_NODES Function Parameters

| Parameter | Description   |
|:----------|:--------------|
| `node`    | Node name     |
| `inst`    | Instance name |

#### 138.5.17 SET_CURRENT_OPINST Procedure

This procedure sets the node name and instance to get the inventory details specific to it in an Oracle Real Application Clusters (RAC) environment.

##### Syntax

    DBMS_QOPATCH.SET_CURRENT_OPINST (
       node_name    IN VARCHAR2 DEFAULT NULL,
       inst_name    IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 138-15 SET_CURRENT_OPINST Procedure Parameters

| Parameter   | Description      |
|:------------|:-----------------|
| `node_name` | Name of node     |
| `inst_name` | Name of instance |
