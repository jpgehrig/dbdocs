Oracle provides guidance for troubleshooting Oracle Label Security tasks.

- Invalid SYS.OLS_ENFORCEMENT and SYS.LBAC_EXP Packages
  If the `SYS.OLS_ENFORCEMENT` and `SYS.LBAC_EXP` PL/SQL packages are invalid, then Oracle Label Security may not have been installed correctly.
- Addressing ORA-6550 and ORA-942 Errors
  The `ORA-6550` and `ORA-942` errors indicate that the Oracle Label Security component of the Oracle Database upgrade is invalid.

**Parent topic:** [Appendixes](part4.md)

### I.1 Invalid SYS.OLS_ENFORCEMENT and SYS.LBAC_EXP Packages

If the `SYS.OLS_ENFORCEMENT` and `SYS.LBAC_EXP` PL/SQL packages are invalid, then Oracle Label Security may not have been installed correctly.

To remedy this problem, you must validate the `SYS.OLS_ENFORCEMENT` and `SYS.LBAC_EXP` package objects.

1.  Log into the PDB as a user who has the `SYSDBA` administrative privilege.
    To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.
2.  Run the following command to validate the two packages.
        @?/rdbms/admin/catols.sql
3.  Run the following commands:
        EXEC LBACSYS.CONFIGURE_OLS
        EXEC LBACSYS.OLS_ENFORCEMENT.ENABLE_OLS
4.  Restart the database instance.
5.  Check the `INVALID` objects to see if the above two items are still listed.
6.  If Oracle Label Security must be disabled after you validate these objects, then do the following:
    1.  Disable Oracle Label Security.
            EXEC LBACSYS.OLS_ENFORCEMENT.DISABLE_OLS;
    2.  Restart the database.

**Parent topic:** Troubleshooting Oracle Label Security

### I.2 Addressing ORA-6550 and ORA-942 Errors

The `ORA-6550` and `ORA-942` errors indicate that the Oracle Label Security component of the Oracle Database upgrade is invalid.

The errors occur during the execution of the `catuppst.sql` script. The following errors are encountered:

    catuppst.sql unable to run in Database: XXXX   Id: 0
    ERRORS FOUND: during upgrade CATCTL ERROR COUNT=5
    ------------------------------------------------------
    Identifier OLS 23-01-10 01:44:51 Script =
    /release/orabase/oracle/rdbms/admin/ols
    ERROR = [ORA-06550: line 119, column 41: PL/SQL: ORA-00942: table or view
    does not exist
    ORA-06550: line 118, column 5:
    PL/SQL: SQL Statement ignored

1.  Log into the PDB as a user who has the `SYSDBA` administrative privilege.
    To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.
2.  Disable and then reenable Oracle Label Security.
3.  Recompile the objects.
        @$ORACLE_HOME/rdbms/admin/utlrp.sql
4.  Run the following procedure to validate Oracle Label Security:
        EXECUTE SYS.VALIDATE_OLS;
5.  If `utlrp.sql` compiles all the Oracle Label Security (`LDAPSYS`) objects successfully, and there are no errors during compilation, then run the following procedure:
        EXEC DBMS_REGISTRY.VALID('OLS');

**Parent topic:** Troubleshooting Oracle Label Security
