## Combined Oracle Grid Infrastructure and Oracle Database Patching

When you patch an Oracle Grid Infrastructure deployment, Oracle FPP enables you to simultaneously patch the Oracle Database homes on the cluster, so you can patch both types of software homes in a single maintenance operation.

**Note:**

You cannot patch both Oracle Grid Infrastructure and Oracle Database in combination with Oracle Fleet Patching and Provisioning (Oracle FPP) Local Mode.

The following optional parameters of the `rhpctl move gihome` command are relevant to the combined Oracle Grid Infrastructure and Oracle Database patching use case:

- `-auto`: Automatically patch databases along with patching Oracle Grid Infrastructure

- `-dbhomes ``mapping_of_Oracle_homes`: Mapping of source and destination working copies in the following format:
      sourcewc1=destwc1,...,source_oracle_home_path=destwcN

- `-dblist ``db_name_list`: Patch only the specified databases

- `-excludedblist ``db_name_list`: Patch all databases except the specified databases

- `-nodatapatch`: Indicates that `datapatch` is not be run for databases being moved

As an example, assume that an Oracle FPP Server with Oracle Grid Infrastructure 19c (19.20) has provisioned the following working copies on an Oracle Grid Infrastructure 19c (19.19) `rhpclient`-less target cluster which includes the node `test_749`:

- `WC_1919_fppc03`: The active Grid home on the Oracle Grid Infrastructure 19c (19.19) cluster

- `WC_GI_1920_fppc03`: A software-only Grid home on the Oracle Grid Infrastructure 19c (19.20) cluster

- `WC_DB_1919_fppc03`: An Oracle RAC 19c (19.19) database home running database instances

- `WC_DB_1920_fppc03`: An Oracle RAC 19c (19.20) database home with no database instances (this is the patched home)

- `WC_DB_1920_fppc03`: An Oracle RAC 19c (19.20) database home running database instances

- `WC_DB_1920_220719_fppc03`: An Oracle RAC 19c (19.20) database home with no database instances (this is the patched home)

Further assume that you want to simultaneously move

- Oracle Grid Infrastructure from working copy `WC_1919_fppc03` to working copy `WC_GI_1920_fppc03`

- Oracle RAC Database `db1` from working copy `WC_DB_1919_fppc03` to working copy `WC_DB_1920_fppc03`

- Oracle RAC Database `db2` in working copy `WC_DB_1920_fppc03` to working copy `WC_DB_1920_220719_fppc03`

The following single command accomplishes the moves:

    $ rhpctl move gihome -destwc WC_GI_1920_fppc03 -sourcewc WC_1919_fppc03
    -auto -dbhomes WC_DB_1919_fppc03=WC_DB_1920_fppc03,WC_DB_1920_fppc03=WC_DB_1920_220719_fppc03

**Notes:**

- If you have an existing Oracle home that is not currently a working copy, then specify the Oracle home path instead of the working copy name for the source home. In the preceding example, if the Oracle home path for an existing 19.19 home is `/u01/app/prod/19.19.0/dbhome1`, then replace `WC_DB_1919_fppc03=WC_DB_1920_fppc03` with `/u01/app/prod/19.20.0/dbhome1=WC_DB_1920_fppc03`.

- If the move operation fails at some point before completing, then you can either resolve the cause of the failure and resume the operation by rerunning the command, or you can undo the partially completed operation by issuing the following command, which restores the configuration to its initial state:
      $ rhpctl move gihome -destwc WC_GI_1920_fppc03 -revert {authentication_option}

In the preceding command example, the Oracle Grid Infrastructure 19c Grid home moves from working copy `WC_1919_fppc03` to working copy `WC_GI_1920_fppc03`, databases running on working copy `WC_DB_1919_fppc03` move to working copy `WC_DB_1920_fppc03`, and databases running on working copy `WC_DB_1920_fppc03` move to working copy `WC_DB_1920_220719_fppc03`.

For each node in the client cluster, RHPCTL:

1.  Runs any configured pre-operation user actions for moving the Oracle Grid Infrastructure (`move gihome`).

2.  Runs any configured pre-operation user actions for moving the database working copies (`move database`).

3.  Stops services running on the node, and applies drain and disconnect options.

4.  Performs the relevant patching operations for Oracle Clusterware and Oracle Database.

5.  Runs any configured post-operation user actions for moving the database working copies (`move database`).

6.  Runs any configured post-operation user actions for moving the Oracle Grid Infrastructure working copy (`move gihome`).

**Related Topics**

- [rhpctl move gihome](gihome-commands.md)

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
